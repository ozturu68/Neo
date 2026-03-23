# KISIM C - Mimari ve Teknik Temel

# Temel Yazılım : \<u>Matrix Ekosistemi\</u>

## Matrix Protokolü

Matrix; gerçek zamanlı iletişim için tasarlanmış, açık ve merkezi olmayan bir standarttır. Tıpkı e-postanın SMTP protokolü üzerine kurulması gibi, Matrix de farklı sunucular ve istemciler arasında güvenli iletişimi standartlaştırır. Projenin güvenlik altyapısının tamamı bu protokolden miras alınmaktadır.

**Şifreleme:** Olm (1:1 oturumlar) ve Megolm (grup oturumları) kütüphaneleri. Signal protokolüyle aynı kriptografik temelden gelir. Bağımsız güvenlik denetiminden geçmiştir.

**Referanslar:** NATO, Almanya Bundeswehr, Fransa hükümeti (Tchap), İngiltere hükümeti, BM Bilişim Merkezi, ABD Uzay Kuvvetleri — 35'ten fazla ülkede kurumsal kullanım.

### Repository Envanteri

| Repository                | Teknoloji        | Açıklama                               | Neo Önceliği | Bileşen             |
| ------------------------- | ---------------- | -------------------------------------- | ------------ | ------------------- |
| cinnyapp/cinny            | TypeScript/React | Web İstemcisi - fork alınacak          | 🔴 Kritik    | İstemci             |
| cinnyapp/cinny-desktop    | Tauri (Rust+JS)  | Masaüstü sarmalayıcı — fork alınacak   | 🔴 Kritik    | Masaüstü            |
| element-hq/synapse        | Python           | Matrix homeserver — Docker ile kurulum | 🔴 Kritik    | Homeserver          |
| livekit/livekit           | Go               | WebRTC SFU medya sunucusu              | 🔴 Kritik    | Ses/Video           |
| element-hq/lk-jwt-service | Go               | LiveKit ↔ Synapse auth köprüsü         | 🔴 Kritik    | JWT Köprüsü         |
| element-hq/element-call   | TypeScript       | Element Call widget (gömülü)           | 🟡 Yüksek    | Ses/Video İstemcisi |
| matrix-org/matrix-js-sdk  | TypeScript       | Cinny'nin kullandığı SDK               | 🟡 Yüksek    | Matrix SDK          |

### Teknoloji Yığını Özeti



```
SUNUCU TARAFI
├── Homeserver          : Synapse (Python) — Matrix protokolü
├── Veritabanı          : PostgreSQL
├── Medya depolama      : Synapse media store (yerel disk)
├── Ses/Video SFU       : LiveKit
├── JWT Auth Köprüsü    : lk-jwt-service
├── Reverse Proxy       : Nginx
└── Deployment          : Docker Compose

İSTEMCİ TARAFI
├── Web istemcisi       : Cinny (React/TypeScript) — Neo fork'u
├── Masaüstü sarmalayıcı: Tauri (Rust + WebView)
├── Ses/Video           : Element Call (widget, gömülü)
├── Şifreleme SDK       : matrix-js-sdk (Olm/Megolm dahil)
└── Paket               : .deb (Tauri otomatik üretir)
```

# Sistem Mimarisi : 

### Bağlantı Mimarisi

```
┌─────────────────────────────────────────────────────────┐
│                      KULLANICI                          │
│          Pardus 25 — Neo Masaüstü (.deb)        │
└──────────────────────┬──────────────────────────────────┘
                       │ HTTPS / WSS (TLS 1.3)
                       ▼
┌─────────────────────────────────────────────────────────┐
│                    CLOUDFLARE                           │
│       CDN + DDoS Koruması + Bot Koruması                │
│       TLS Sonlandırma + TURN/TLS Fallback               │
└──────────────────────┬──────────────────────────────────┘
                       │ Cloudflare Tunnel (cloudflared)
                       ▼
┌─────────────────────────────────────────────────────────┐
│              FİZİKSEL SUNUCU (Türkiye)                  │
│                                                         │
│  ┌──────────────────────────────────────────────────┐   │
│  │   UFW Güvenlik Duvarı                            │   │
│  │   (Yalnızca SSH + Cloudflare IP aralıkları)      │   │
│  └──────────────────────┬───────────────────────────┘   │
│                         │                               │
│  ┌──────────────────────▼───────────────────────────┐   │
│  │   Nginx — Reverse Proxy                          │   │
│  │   HSTS · CSP · X-Frame-Options · Rate Limiting   │   │
│  └──┬──────────────┬────────────────┬───────────────┘   │
│     │              │                │                   │
│  ┌──▼──────┐  ┌────▼──────┐  ┌─────▼──────┐             │
│  │  Cinny  │  │  Synapse  │  │  LiveKit   │             │
│  │  Web    │  │  :8008    │  │  SFU       │             │
│  └─────────┘  └────┬──────┘  └─────┬──────┘             │
│                    │               │                    │
│               ┌────▼──────┐  ┌─────▼──────┐             │
│               │ PostgreSQL│  │ lk-jwt     │             │ 
│               │ (iç ağ)   │  │ service    │             │
│               └───────────┘  └────────────┘             │
│                                                         │
│  ┌──────────────────────────────────────────────────┐   │
│  │   fail2ban   │   cloudflared   │   log yönetimi  │   │
│  └──────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────┘
```

### Neden Cloudflare Tunnel ?

Sunucu fiziksel bir makine, ISP'den statik IP veya port yönlendirmesi garanti edilemiyor. Cloudflare Tunnel ile sunucunun genel IP'ye veya herhangi bir port açımına ihtiyacı olmaz. Cloudflare hem CDN hem DDoS koruma kalkanı hem de otomatik TLS görevi görür. Ücretsiz tier, demo için fazlasıyla yeterlidir.

### Domain Yapısı

| Subdomain        | Yönlendirme        | Açıklama                   |
| ---------------- | ------------------ | -------------------------- |
| `app.domain`     | → Cinny web        | İstemci web arayüzü        |
| `matrix.domain`  | → Synapse :8008    | Matrix homeserver API      |
| `element.domain` | → Element Call     | Ses/video görüşme widget'ı |
| `rtc.domain`     | → LiveKit + lk-jwt | WebRTC SFU + auth köprüsü  |

### Ses/Video Bağlantı Stratejisi

Cloudflare Tunnel yalnızca HTTP/HTTPS (TCP) trafiğini tünelleyebildiğinden WebRTC'nin tercih ettiği UDP trafiği doğrudan geçemez. Bu durum şu fallback zinciriyle çözülür:

```
1. ICE/UDP   (50000-50100)  → En iyi performans, UDP port açıksa aktif
2. TURN/TLS  (TCP 443)      → Cloudflare Tunnel üzerinden çalışır ✓
3. ICE/TCP   (TCP 7881)     → İkincil fallback

Demo fazında yalnızca TURN/TLS yeterlidir.
UDP portları ilerleyen aşamada ISP ile çözülerek performans artırılır.
```

# Donanım Envanteri : 

### Geliştirici Makinesi (Laptop)

| Özellik         | Değer                                                   |
| --------------- | ------------------------------------------------------- |
| İşlemci         | Intel i5 12. Nesil H serisi                             |
| Ekran Kartı     | NVIDIA RTX 3050 4 GB                                    |
| RAM             | 16 GB                                                   |
| Depolama        | 1 TB SSD                                                |
| İşletim Sistemi | Fedora KDE (latest stable)                              |
| IDE             | Visual Studio Code                                      |
| Eklenti         | Kilo Code                                               |
| AI Erişimi      | Kilo Code Provider ( Minimax 2.5 - Deepseek Reasoner )  |

### Demo / Üretim Sunucusu

| Özellik         | Değer                              | Not                                                                  |
| --------------- | ---------------------------------- | -------------------------------------------------------------------- |
| İşlemci         | Intel i5 2. Nesil                  | Düşük güç tüketimi, sanallaştırma desteği var                        |
| RAM             | 16 GB                              | Docker servisleri için yeterli                                       |
| Depolama        | 300 GB HDD                         | Performans darboğazı olabilir (SSD'ye yükseltme değerlendirilebilir) |
| Ekran Kartı     | Yok                                | WebRTC işlemleri CPU üzerinden yürütülecek                           |
| İşletim Sistemi | Ubuntu Server 24.04 LTS (önerilen) | Bkz. ADR-002                                                         |
| Bağlantı        | Cloudflare Tunnel                  | Bkz. ADR-003                                                         |
| Erişilebilirlik | Mevcut, geliştirmeye hazır         |                                                                      |

**Kritik Performans Notu:** i5 2. nesil işlemci + HDD kombinasyonu, 10 kullanıcılı eş zamanlı sesli/görüntülü görüşmede en yüksek risk faktörüdür. Milestone 3'te erken yük testi zorunludur. Gerekirse depolama SSD'ye yükseltilebilir.

# Güvenlik Mimarisi : 

Bu bölüm projenin en kritik teknik bölümüdür. Güvenlik, eklenti değil temeldir.

### Güvenlik Katmanları

```
KATMAN 1 — AĞ ALTYAPI GÜVENLİĞİ
├── TLS 1.3 (Cloudflare üzerinden zorunlu)
├── HSTS (HTTP Strict Transport Security)
├── Güvenlik başlıkları (CSP, X-Frame-Options, Permissions-Policy vb.)
├── DDoS koruması (Cloudflare)
├── Bot koruması (Cloudflare)
└── UFW: Yalnızca SSH + Cloudflare IP aralıkları açık

KATMAN 2 — SUNUCU SERTLEŞTİRME
├── fail2ban: SSH + Synapse giriş denemesi izleme
├── Nginx rate limiting
├── Docker iç ağı: PostgreSQL dışa kapalı
├── .env dosyası: Sırlar docker-compose'da plain text değil
└── Unattended-upgrades: Otomatik güvenlik güncellemeleri

KATMAN 3 — KİMLİK DOĞRULAMA GÜVENLİĞİ
├── Synapse kayıt kapalı (yalnızca davet ile üyelik)
├── Synapse rate limiting (giriş denemesi sınırlama)
├── Güçlü şifre politikası (Synapse password_config)
├── JWT token güvenliği (lk-jwt-service)
└── Synapse admin API yalnızca iç ağda erişilebilir

KATMAN 4 — VERİ GÜVENLİĞİ
├── E2EE: Olm/Megolm (Matrix protokolü, varsayılan aktif)
├── TLS: Tüm istemci-sunucu trafiği şifreli
├── PostgreSQL: Yalnızca iç Docker ağında erişilebilir
├── Medya dosyaları: Synapse erişim kontrolü altında
└── At-rest encryption: Değerlendirme aşamasında

KATMAN 5 — UYGULAMA GÜVENLİĞİ
├── Cinny: 0 açık güvenlik bildirimi (GitHub Security)
├── Synapse: Güncel sürüm, bilinen CVE'ler kapalı
├── Dependency taraması: npm audit + pip-audit
└── Content Security Policy: XSS koruması

KATMAN 6 — İZLEME VE YANIT
├── Docker container log yönetimi
├── Synapse access log analizi
├── fail2ban aktif blok izleme
└── Düzenli yedekleme (PostgreSQL dump)
```

### Matrix Güvenlik Avantajı

Stoat Chat yaklaşımından farklı olarak Neo, güvenlik açığı kapatmaya değil güvenlik mirasına dayanır. Matrix'in E2EE implementasyonu bağımsız olarak denetlenmiş ve üretimde kanıtlanmıştır. Geliştirici zamanı güvenlik icat etmeye değil, Pardus'a özgü değer katmaya harcanır.
