# Proje Ana Dokümantasyonu

* Versiyon    : 2.0.0
* Tarih       : 15 Mart 2026
* Yazar       : Muzaffer Umut Öztürk
* Durum       : Aktif Geliştirme - Platform Değişikliği Sonrası
* Bağlam      : Teknofest 2026 / Pardus Hata Yakalama ve Öneri Yarışması
* Lisans      : AGPL-3.0



# İÇİNDEKİLER

KISIM A — PROJE TANIMI

&#x20; A1. Yönetici Özeti

&#x20; A2. Proje Şartı

&#x20; A3. Proje Felsefesi ve Yaklaşımı

KISIM B — GEREKSİNİMLER

&#x20; B1. Problem Tanımı

&#x20; B2. Fonksiyonel Gereksinimler

&#x20; B3. Fonksiyonel Olmayan Gereksinimler

&#x20; B4. Kapsam Sınırları

KISIM C — MİMARİ VE TEKNİK TEMEL

&#x20; C1. Temel Yazılım: Matrix Ekosistemi

&#x20; C2. Sistem Mimarisi

&#x20; C3. Donanım Envanteri

&#x20; C4. Güvenlik Mimarisi

KISIM D — PROJE YÖNETİMİ

&#x20; D1. Yol Haritası ve Milestone'lar

&#x20; D2. Risk Kayıt Defteri

&#x20; D3. Başarı Kriterleri

KISIM E — KARAR GÜNLÜĞÜ (ADR)

KISIM F — DEĞİŞİKLİK GÜNLÜĞÜ (CHANGELOG)



# Sistem Bilgileri 

ozturu68@fedora:\~/Projeler/TEKNOFEST/Pardus\$ ls -l

toplam 0

drwxr-xr-x. 1 ozturu68 ozturu68 44 Mar 16 18:43 NEO

drwxr-xr-x. 1 ozturu68 ozturu68 474 Mar 21 23:29 'Neo - docs'

ozturu68@fedora:\~/Projeler/TEKNOFEST/Pardus\$ fastfetch

&#x20;.',;::::;,'.ozturu68@fedora

&#x20;.';:cccccccccccc:;,.---------------

&#x20;.;cccccccccccccccccccccc;.OS: Fedora Linux 43 (KDE Plasma Desktop Edition) x86\_64

&#x20;.:cccccccccccccccccccccccccc:.Host: EXCALIBUR G770 (Type1Version)

&#x20;.;ccccccccccccc;.:dddl:.;ccccccc;.Kernel: Linux 6.19.8-200.fc43.x86\_64

&#x20;.:ccccccccccccc;OWMKOOXMWd;ccccccc:.Uptime: 3 hours, 51 mins

.:ccccccccccccc;KMMc;cc;xMMc;ccccccc:.Packages: 3063 (rpm), 41 (flatpak)

,cccccccccccccc;MMM.;cc;;WW:;cccccccc,Shell: bash 5.3.0

:cccccccccccccc;MMM.;cccccccccccccccc:Display (VY279HGR): 1920x1080 in 27", 100 Hz \[External]

:ccccccc;oxOOOo;MMM000k.;cccccccccccc:Display (NCP004D): 1920x1080 in 16", 144 Hz \[Built-in] \*

cccccc;0MMKxdd:;MMMkddc.;cccccccccccc;DE: KDE Plasma 6.6.3

ccccc;XMO';cccc;MMM.;cccccccccccccccc'WM: KWin (Wayland)

ccccc;MMo;ccccc;MMW.;ccccccccccccccc;WM Theme: Breeze

ccccc;0MNc.ccc.xMMd;ccccccccccccccc;Theme: Breeze (Dark) \[Qt], Breeze-Dark \[GTK2], Breeze \[GTK3]

cccccc;dNMWXXXWM0:;cccccccccccccc:,Icons: breeze-dark \[Qt], breeze-dark \[GTK2/3/4]

cccccccc;.:odl:.;cccccccccccccc:,.Font: Noto Sans (10pt) \[Qt], Noto Sans (10pt) \[GTK2/3/4]

ccccccccccccccccccccccccccccc:'.Cursor: breeze (24px)

:ccccccccccccccccccccccc:;,..Terminal: konsole 25.12.3

&#x20;':cccccccccccccccc::;,.CPU: 12th Gen Intel(R) Core(TM) i5-12450H (12) @ 4.40 GHz

GPU 1: NVIDIA GeForce RTX 3050 Mobile \[Discrete]

GPU 2: Intel UHD Graphics @ 1.20 GHz \[Integrated]

Memory: 6.74 GiB / 15.35 GiB (44%)

Swap: 2.06 GiB / 8.00 GiB (26%)

Disk (/): 287.18 GiB / 928.91 GiB (31%) - btrfs

Local IP (wg0-mullvad): 10.155.164.100/32

Battery (Primary): 95% \[AC Connected]

Locale: tr\_TR.UTF-8







ozturu68@fedora:\~/Projeler/TEKNOFEST/Pardus\$ nvidia-smi

Mon Mar 23 16:01:34 2026 

+-----------------------------------------------------------------------------------------+

\| NVIDIA-SMI 580.126.18 Driver Version: 580.126.18 CUDA Version: 13.0 |

+-----------------------------------------+------------------------+----------------------+

\| GPU Name Persistence-M | Bus-Id Disp.A | Volatile Uncorr. ECC |

\| Fan Temp Perf Pwr:Usage/Cap | Memory-Usage | GPU-Util Compute M. |

\| | | MIG M. |

|=========================================+========================+======================|

\| 0 NVIDIA GeForce RTX 3050 ... Off | 00000000:01:00.0 On | N/A |

\| N/A 45C P8 4W / 60W | 43MiB / 4096MiB | 22% Default |

\| | | N/A |

+-----------------------------------------+------------------------+----------------------+



+-----------------------------------------------------------------------------------------+

\| Processes: |

\| GPU GI CI PID Type Process name GPU Memory |

\| ID ID Usage |

|=========================================================================================|

\| 0 N/A N/A 6030 G /usr/bin/kwin\_wayland 1MiB |

+-----------------------------------------------------------------------------------------+

ozturu68@fedora:\~/Projeler/TEKNOFEST/Pardus\$ 





# KISIM A - Proje Tanımı

# Yönetici Özeti : 

Neo; Türkiye'nin milli işletim sistemi Pardus'a derin entegrasyon ile çalışan, uçtan uca şifreli, sesli ve görüntülü görüşme destekli, açık kaynaklı, merkezi bir iletişim platformudur.

Proje; dünyada NATO, Bundeswehr ve onlarca ulusal hükümet tarafından güvenilen **Matrix açık protokolü** ile bu protokolün üzerine inşa edilmiş **Cinny** istemcisini temel alır. Cinny fork'u olarak geliştirilecek Neo istemcisi; Pardus görsel kimliğiyle markalaştırılacak, tam Türkçe arayüze kavuşacak ve Tauri ile `.deb` paketi olarak dağıtılacaktır. Sunucu tarafında **Synapse** homeserver, **LiveKit SFU** ses/video altyapısı ve **PostgreSQL** veritabanı Docker Compose ile Türkiye'deki fiziksel sunucuda çalıştırılacaktır.

Bu yaklaşımın kritik farkı şudur: güvenlik sıfırdan inşa edilmesi gereken bir katman değil, temelin ta kendisidir. Matrix'in Olm/Megolm şifreleme protokolü bağımsız güvenlik denetiminden geçmiş, gerçek dünyada kanıtlanmış bir altyapıdır. Neo bu altyapıyı miras alır; geliştirici zamanı güvenliği icat etmeye değil, Pardus ekosistemiyle özgün entegrasyona harcanır.

**Kritik bağlam:** Projenin tüm teknik geliştirmesi tek bir geliştirici tarafından yürütülecektir. Proje yönetimi yapay zeka desteğiyle sağlanacak, geliştirme ise laptop üzerinde gerçekleştirilecektir.

**Demo hedefi:** 10 eş zamanlı kullanıcıyla stabil çalışan; mesajlaşma, dosya paylaşımı, sesli ve görüntülü görüşme özelliklerini kapsayan; E2EE varsayılan olarak aktif; Pardus 25 üzerinde `.deb` ile kurulabilen bir platform.

# Proje Şartı : 

### Kimlik

| Alan                     | Değer                                                                           |
| ------------------------ | ------------------------------------------------------------------------------- |
| Proje Adı                | Neo                                                                             |
| İstemci Temeli           | Cinny (Matrix İstemcisi) - fork                                                 |
| İstemci GitHub           | github.com/cinnyapp/cinny                                                       |
| Masaüstü Temeli          | Cinny Desktop (Tauri) — fork                                                    |
| Masaüstü GitHub          | github.com/cinnyapp/cinny-desktop                                               |
| Sunucu Protokolü         | Matrix (açık standart)                                                          |
| Homeserver               | Synapse                                                                         |
| Ses/Video Altyapısı      | LiveKit SFU + Element Call                                                      |
| Lisans                   | AGPL-3.0                                                                        |
| Hedef Platform           | Pardus 25 "Bilge" (Debian 13 tabanlı)                                           |
| Hedef Masaüstü Ortamları | GNOME 48 (birincil), XFCE 4.20 (ikincil)                                        |
| Demo Hedefi              | 10 eş zamanlı kullanıcı                                                         |
| Deadline                 | 15 Mayıs 2026                                                                   |
| Yarışma                  | Teknofest 2026 — Pardus Hata Yakalama ve Öneri Yarışması, Geliştirme Kategorisi |

### Paydaşlar

| Rol                       | Kişi                        | Sorumluluk                                           |
| ------------------------- | --------------------------- | ---------------------------------------------------- |
| Proje Yöneticisi          | Muzaffer Umut Öztürk        | Tüm kararlar, strateji, önceliklendirme              |
| Proje Yönetici Yardımcısı | Claude (Anthropic)          | Dokümantasyon, analiz, araştırma, mimari danışmanlık |
| Yazılımcı                 | Laptop Sistemi (Fedora KDE) | Kod geliştirme, derleme, test                        |
| Danışman Öğretmen         | Ayşen Alçakır               | Akademik rehberlik, yarışma koordinasyonu            |

### Geliştirme Ortamı

| Donanım                  | Yazılım                                  |   |
| ------------------------ | ---------------------------------------- | - |
| İ5 12. nesil H işlemci   | Fedora KDE Latest Stable İşletim Sistemi |   |
| RTX 3050 4GB ekran kartı | Visual Studio Code geliştirme ortamı     |   |
| 16GB DDR4 RAM            | Kilo Code eklentisi                      |   |
| 1TB SSD                  | Docker ile sunucular                     |   |
| Excalibur G770 Laptop    | -                                        |   |

### Vizyon

> "Pardus işletim sistemi kullanıcıları için; verisi Türkiye'de tutulan, uçtan uca şifreli, sesli ve görüntülü iletişim destekli, açık kaynaklı ve yerli sunucuda çalışan güvenli bir iletişim platformu."

### Misyon

> "Pardus'u, güvenli ve egemen bir iletişim altyapısıyla bütünleşik bir iş ve yaşam istasyonuna dönüştürmek; kullanıcıları yabancı veri işlemcilerinden bağımsız kılmak."

# Proje Felsefesi ve Yaklaşımı : 

Bu bölüm, projenin ruhunu tanımlar. Gelecekte alınacak her teknik karar bu felsefeyle tutarlı olmalıdır.

### Neo güvenliği icat etmez, miras alır

Piyasadaki pek çok "güvenli" iletişim projesi güvenlik katmanını sıfırdan yazmaya çalışır. Bu yaklaşım hem riskli hem de zaman tüketicidir. Neo farklı bir strateji izler: bağımsız güvenlik denetiminden geçmiş, NATO ve onlarca hükümet tarafından üretimde kullanılan Matrix protokolünü temel alır. Olm/Megolm şifreleme kütüphanesi Signal ile aynı kriptografik temelden gelir ve bu güvenlik Neo'ya miras yoluyla geçer.

Geliştirici zamanı bu sayede asıl değere odaklanabilir: Pardus ekosistemiyle özgün entegrasyon, Türkçe kullanıcı deneyimi ve yerel sunucu egemenliği.

### Güvenlik birinci prensip, son adım değil

Güvenlik geliştirmenin sonunda "eklenen" bir katman değildir. Matrix protokolünü temel almak bu prensibin mimariye yansımasıdır. E2EE varsayılan olarak gelir; sunucu yapılandırmasında her katmanda güvenlik önlemleri uygulanır; tüm geliştirmeler bu perspektifle değerlendirilir.

### Dürüst kapsam yönetimi

Tek geliştirici ve sınırlı donanım gerçeklerini görmezden gelmenin bedeli projenin tamamını riske atmaktır. Her milestone'da kapsam gerçekçi tutulur. Bir özellik demo süresinde tamamlanamayacaksa açıkça belgelenir ve sonraki versiyona planlanır.

### Geliştirme yaklaşımı: Katmanlı analiz ve inşa

```
YAKLAŞIM HİYERARŞİSİ

Önce çalıştır, sonra özelleştir.
Önce güvenliği doğrula, sonra markalaştır.
Önce test et, sonra entegre et.

Katman 0 — Sunucu Altyapısı   (Synapse + PostgreSQL + Docker)
Katman 1 — Ses/Video Altyapısı (LiveKit SFU + lk-jwt-service)
Katman 2 — Güvenlik Sertleştirme (UFW, Nginx, fail2ban, Synapse hardening)
Katman 3 — İstemci Fork'u      (Cinny klonu, temel değişiklikler)
Katman 4 — Markalaştırma       (Pardus kimliği, Türkçe, özel özellikler)
Katman 5 — Paketleme           (Tauri .deb, Pardus 25 entegrasyon)
```

Her katman önce çalışır hale getirilir, sonra bir üst katmana geçilir.

# KISIM B - Gereksinimler

# Problem Tanımı : 

Pardus; TÜBİTAK BİLGEM/YTE tarafından geliştirilen, Debian tabanlı Türkiye'nin milli işletim sistemidir. Kamu kurumlarından üniversitelere, bireysel kullanıcılara kadar geniş bir kitleye hitap eder. Ancak Windows ve macOS'un aksine, Pardus ekosisteminde **entegre bir iletişim platformu yoktur.**

Pardus kullanıcıları; anlık mesajlaşma, sesli/görüntülü görüşme ve dosya paylaşımı için Microsoft Teams, Zoom, WhatsApp veya Telegram gibi yabancı platformlara mecbur kalmaktadır. Bu durum yapısal riskler doğurur:

* Kurumsal yazışmalar ve veriler yabancı sunucularda işlenir ve saklanır
* KVKK kapsamında yurt dışı veri aktarımı hukuki sorun oluşturur
* Reklam destekli platformlar kullanıcı verisini işler
* Yabancı şirket kararları anlık erişim kesintisine yol açabilir
* Pardus deneyimi iletişim katmanında bütünleşik değildir

Matrix protokolü üzerine inşa edilecek ve Türkiye'deki fiziksel sunucuda çalışacak Neo, bu risklerin tamamını giderme potansiyeline sahiptir. Matrix; NATO, Bundeswehr, Fransa ve Almanya hükümetleri tarafından üretimde kullanılan, bağımsız güvenlik denetiminden geçmiş bir açık standarttır.

# Fonksiyonel Gereksinimler : 

### Demo için zorunlu 

| #   | Gereksinim                          | Öncelik |
| --- | ----------------------------------- | ------- |
| F1  | Kullanıcı kaydı ve kimlik doğrulama | Kritik  |
| F2  | Özel mesajlaşma (DM)                | Kritik  |
| F3  | Grup kanalları ve sunucu yapısı     | Kritik  |
| F4  | Dosya paylaşımı                     | Kritik  |
| F5  | E2EE (en az DM katmanında)          | Kritik  |
| F6  | Sesli görüşme                       | Kritik  |
| F7  | Görüntülü görüşme                   | Kritik  |
| F8  | Ekran paylaşma                      | Kritik  |
| F9  | Türkçe arayüz                       | Yüksek  |
| F10 | Masaüstü bildirimleri               | Yüksek  |
| F11 | Kullanıcı profil yönetimi           | Yüksek  |

### Demo sonrası (ileriki sürümler)

| #   | Gereksinim                                    |
| --- | --------------------------------------------- |
| F12 | Mobil uygulama (Android/iOS) Neo markalaşması |
| F13 | Federasyon / çoklu sunucu desteği             |
| F14 | Sesli/görüntülü için E2EE                     |
| F15 | Bot API'si                                    |
| F16 | Pardus resmi uygulama deposuna dagil edilme   |

# Fonksiyonel Olmayan Gereksinimler :

| Alan              | Gereksinim              | Hedef Metrik                                                  |
| ----------------- | ----------------------- | ------------------------------------------------------------- |
| Performans        | Demo ortamı kararlılığı | 10 eş zamanlı kullanıcı, <200ms mesaj gecikmesi               |
| Güvenlik          | Şifreleme               | TLS 1.3 zorunlu, E2EE aktif                                   |
| Güvenlik          | Sunucu sertleştirme     | UFW, fail2ban, Nginx güvenlik başlıkları, rate limiting aktif |
| Güvenlik          | Kimlik doğrulama        | Synapse kayıt kapalı (davet sistemi), rate limiting aktif     |
| Veri Egemenliği   | Veri konumu             | Tüm veriler Türkiye'deki fiziksel sunucuda                    |
| Uyumluluk         | İşletim sistemi         | Pardus 25 GNOME ve XFCE'de çalışır                            |
| Uyumluluk         | Kurulum                 | `sudo apt install ./pardus-akis.deb` ile kurulabilir          |
| Uyumluluk         | Yasal                   | KVKK uyumlu, AGPL-3.0 lisans gereklilikleri karşılanmış       |
| Sürdürülebilirlik | Kaynak kod              | Tüm değişiklikler kamuya açık, belgelenmiş                    |

# Kapsam Sınırları : 

### Kapsam İçi

* Cinny istemcisinin fork'lanarak Neo olarak markalaştırılması
* Cinny Desktop (Tauri) fork'unun `.deb` paketi olarak derlenmesi
* Synapse homeserver kurulumu, yapılandırması ve güvenlik sertleştirmesi
* PostgreSQL veritabanı kurulumu ve yapılandırması
* LiveKit SFU kurulumu ve Element Call entegrasyonu
* Nginx reverse proxy güvenlik yapılandırması
* Cloudflare Tunnel entegrasyonu
* UFW + fail2ban sunucu güvenliği
* Tam Türkçe arayüz (Cinny çeviri altyapısı kullanılarak)
* Pardus görsel kimliği (logo, renk paleti, ikonlar)
* Atatürk köşesi özel bileşeni
* Hakkında, takım ve lisans ekranları
* Tüm geliştirmelerin belgelenmesi (AGPL-3.0 zorunluluğu)

### Kapsam Dışı

* Matrix protokolünde herhangi bir değişiklik veya geliştirme
* Synapse kaynak kodunda değişiklik
* Mobil uygulama Neo markalaşması (ileriki sürüm)
* Federasyon ve çoklu sunucu desteği (ileriki sürüm)
* Sesli/görüntülü görüşme için E2EE (MatrixRTC spesifikasyonu olgunlaşınca)
* TÜBİTAK/YTE ile resmi kurumsal logo/marka anlaşması
* Pardus resmi uygulama deposuna dahil edilme (bu sürüm için)

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


# KISIM D - Proje Yönetimi

# Yol Haritası ve Milestona'lar 

* **Başlangıç:** 2 Mart 2026 
* **Deadline:**  2026 
* **Toplam süre:** 

***

### Milestone 0 - Dokümantasyon ve Zemin Hazırlığı 

* [x] Proje Dokümantasyonu oluşturuldu
* [x] Affine proje alanı yapılandırıldı
* [x] Git tarafı yapılandırıldı
* [x] Gerekli dosyalar alındı ve konumlandırıldı 
* [x] Proje dokümantasyonu v2.0.0 olarak güncellendi
* [x] Sunucuya Ubuntu Server LTS kuruldu

***

### Milestone 1 - Analiz ve Ortam Hazırlığı 

* [x] &#x20;Ubuntu Server 24.04 LTS kurulumu ve minimal sertleştirme
* [x] &#x20;Docker ve Docker Compose kurulumu
* [x] &#x20;Nginx kurulumu ve temel yapılandırması
* [x] &#x20;Cloudflare Tunnel kurulumu ve domain yapılandırması
* [x] &#x20;UFW yapılandırması (SSH + Cloudflare IP aralıkları)
* [x] &#x20;fail2ban kurulumu ve yapılandırması
* [x] &#x20;PostgreSQL container kurulumu ve test edilmesi
* [x] &#x20;Synapse homeserver container kurulumu
* [x] &#x20;Synapse temel yapılandırması (kayıt kapalı, rate limiting)
* [x] `matrix.domain` üzerinden Synapse erişimi test edildi
* [x] &#x20;İlk kullanıcı oluşturuldu ve temel mesajlaşma test edildi
* [x] &#x20;Tüm adımlar belgelendi

***

### Milestone 2 - Backend ve Güvenlik Geliştirmeleri 

* [ ] &#x20;LiveKit SFU container kurulumu
* [ ] &#x20;lk-jwt-service container kurulumu
* [ ] &#x20;Synapse ↔ LiveKit entegrasyonu yapılandırıldı
* [ ] &#x20;Element Call widget `element.domain`'de yayınlandı
* [ ] &#x20;TURN/TLS yapılandırması tamamlandı (Cloudflare Tunnel üzerinden)
* [ ] &#x20;1:1 sesli görüşme test edildi
* [ ] &#x20;1:1 görüntülü görüşme test edildi
* [ ] &#x20;Ekran paylaşımı test edildi
* [ ] &#x20;Grup sesli/görüntülü görüşme test edildi (3-5 kullanıcı)
* [ ] &#x20;Tüm adımlar belgelendi

***

### Milestone 3 - Sesli ve Görüntülü Görüşme 

* [ ] &#x20;Nginx güvenlik başlıkları eklendi (HSTS, CSP, X-Frame-Options, Permissions-Policy)
* [ ] &#x20;Nginx rate limiting ince ayarı yapıldı
* [ ] &#x20;Synapse password\_config güçlendirildi
* [ ] &#x20;Docker iç ağ izolasyonu doğrulandı (PostgreSQL dışa kapalı)
* [ ] &#x20;.env dosyası yapılandırması tamamlandı (sırlar plain text değil)
* [ ] &#x20;Unattended-upgrades etkinleştirildi
* [ ] &#x20;Synapse admin API erişim kısıtlaması doğrulandı
* [ ] &#x20;npm audit (Cinny bağımlılıkları) — açık varsa çözüldü
* [ ] &#x20;Bütünleşik güvenlik taraması yapıldı ve belgelendi
* [ ] &#x20;10 eş zamanlı kullanıcı yük testi yapıldı (<200ms mesaj gecikmesi)

***

### Milestone 4 - Geçiş Öncesi Kontroller 

* [ ] &#x20;Cinny reposu fork'landı: `pardus-akis` adıyla
* [ ] &#x20;Cinny Desktop reposu fork'landı
* [ ] `config.json` güncellendi: uygulama adı, varsayılan homeserver
* [ ] `public/` klasörü güncellendi: Pardus logosu, favicon, ikonlar
* [ ] &#x20;CSS değişkenleri güncellendi: Pardus renk paleti
* [ ] &#x20;Giriş ekranı Pardus kimliğine uyarlandı
* [ ] &#x20;Tam Türkçe arayüz tamamlandı (Cinny çeviri altyapısı)
* [ ] `src-tauri/tauri.conf.json` güncellendi: uygulama adı, ikon
* [ ] &#x20;Atatürk köşesi bileşeni tasarlandı ve geliştirildi
* [ ] &#x20;Hakkında ekranı: proje bilgileri, takım, lisans
* [ ] &#x20;Pardus 25 GNOME masaüstü entegrasyonu (.desktop dosyası)
* [ ] &#x20;Pardus 25 XFCE uyumluluğu test edildi

***

### Milestone 5 - Markalaştırma ve Özelleştirme 

* [ ] &#x20;Tauri ile `.deb` paketi derlendi
* [ ] `sudo apt install ./pardus-akis.deb` ile kurulum test edildi
* [ ] &#x20;Pardus 25 GNOME sanal makinede baştan sona test edildi
* [ ] &#x20;Pardus 25 XFCE sanal makinede baştan sona test edildi
* [ ] &#x20;10 eş zamanlı kullanıcı entegrasyon testi (mesajlaşma + ses/video)
* [ ] &#x20;Performans ölçümleri belgelendi
* [ ] &#x20;Bulunan hatalar giderildi

***

### Milestone 6 - Paketleme ve Test Etme 

* [ ] &#x20;Bütünleşik güvenlik taraması yapıldı, belgelendi
* [ ] &#x20;Bütünleşik hata taraması yapıldı, belgelendi
* [ ] &#x20;Sunucu sistemi production'a hazır hale getirildi
* [ ] &#x20;Otomatik yedekleme sistemi kuruldu ve test edildi
* [ ] &#x20;İzleme ve log yönetimi yapılandırıldı

***

### Milestone 7 - Merkezi Sunucu Yapılandırması  Tanıtım sitesi kuruldu

* [ ] &#x20;GitHub sayfası yapılandırıldı (README, ekran görüntüleri)
* [ ] &#x20;Kurulum ve kullanım kılavuzları oluşturuldu
* [ ] &#x20;Sosyal medya tanıtımları yapıldı
* [ ] &#x20;Teknofest 2026 tanıtım sunumu hazırlandı

***

# Risk Kayıt Defteri

| Risk                                   | Olasılık  | Etki   | Azaltma Stratejisi                       |
| -------------------------------------- | --------- | ------ | ---------------------------------------- |
| HDD I/O darboğazı (PostgreSQL)         | Orta      | Yüksek | M3'te yük testi; gerekirse SSD yükseltme |
| LiveKit TURN/TLS performans sorunu     | Düşük     | Orta   | UDP portları açarak fallback kaldırma    |
| Synapse bellek tüketimi (i5-2. nesil)  | Düşük     | Orta   | Synapse cache ayarları optimize edilecek |
| Cinny fork uyumluluk sorunu            | Düşük     | Düşük  | Upstream değişiklikleri takip edilecek   |
| Cloudflare ücretsiz tier kısıtlamaları | Çok Düşük | Düşük  | Demo için tier fazlasıyla yeterli        |

***

# Başarı Kriterleri

| /  | Kriter                                                                                                           |
| -- | ---------------------------------------------------------------------------------------------------------------- |
| M0 | Zemin hazırlığı tamamlanmış, platform kararı belgelenmiş, dokümantasyon güncel                                   |
| M1 | Synapse çalışıyor, temel mesajlaşma ve dosya paylaşımı test edilmiş, tüm güvenlik önlemleri temel seviyede aktif |
| M2 | Sesli görüşme, görüntülü görüşme ve ekran paylaşımı Cloudflare Tunnel üzerinden çalışır durumda                  |
| M3 | Güvenlik katmanları tamamlanmış, yük testleri geçilmiş                                                           |
| M4 | Neo markalaşması tamamlanmış, Türkçe arayüz hazır, Atatürk köşesi dahil                                          |
| M5 | `.deb` paketi üretilmiş, Pardus 25 sanal makinede başarıyla test edilmiş                                         |
| M6 | Sunucu production'a hazır, yedekleme ve izleme aktif                                                             |
| M7 | Tanıtım materyalleri hazır, Teknofest sunumu tamamlanmış                                                         |

***

# KISIM E - Karar Günlüğü (ADR)

***

### ADR-001:Temel Platform Olarak Seçilen Sistem : Stoat Chat

* Tarih : 2 Mart 2026
* Durum : Kabul Edildi
* **Bağlam**: Sınırlı sürede sıfırdan bir sistem, protokol ve ortam kurmak hem zorlayıcı hem de risklidir. Açık kaynaklı, projeye uygun bir sistem belirlenecek ve geliştirilecektir.
* **Karar**: Stoat Chat temel alınacaktır.
* **Sonuçlar**: Hızlı başlangıç, test edilmiş sağlam bir altyapı, geliştirme imkanı yüksek.

***

### ADR-002:Sunucunun İşletim Sistemi : Ubutnu Server Latest Stable

* Tarih : 2 Mart 2026
* Durum : Kabul Edildi
* **Bağlam**: Server makinesi için işletim sistemi gerekli, stabil ve imkanları yüksek olmalı.
* **Karar**: Ubuntu Server Latest Stable işletim sistemi tercih edilecektir.

***

### ADR-003:Sunucu Bağlantısı : Cloudflare 

* Tarih : 2 Mart 2026
* Durum : Kabul Edildi
* **Bağlam**: Statik IP ve port açımı güvenlik açısından riskli ve zahmetlidir, maliyeti düşük, güvenilir, hızlı bir bağlantı sağlayıcı lazım.
* **Karar**: Cloudflared Tunnel Sistemi ile sunucunun dış dünyayla bağlantısı kurulacaktır
* **Sonuçlar**: Cloudflare'e bağımlılık, uzun vadede değerlendirilmedir ancak Cloudflare dünyanın en büyük DNS hizmetlerini sağlayan şirkettir, güvenilirliği kanıtlanmıştır. 

***

### ADR-004:Git Yapılandırması : GitHub 

* Tarih : 4 Mart 2026
* Durum : Kabul Edildi
* **Bağlam**: Geliştiriciler için bir zorunluluk olan git yapılandırmasına ihiyaç var.
* **Karar**: Sisteme github kurulumu ve yapılandırması eklendi, ssh key alındı :
  * **Fedora Laptop**`SHA256:HbDjlQfD6c9nqYRsF/O1q4uQGEYZ/hikBgwf1o5VXkw`
* **Sonuçlar**: Sürüm kontrolü, kod yedeklemesi kolaylaştı, Microsoft'a bağımlılık. Genel olara dışa bağımlılıkların düzeltilmesi için fiziki sunucu donanımının geliştirilmesi gerekmekte. 

***

### ADR-005 — Temel Platform Değişikliği : Matrix + Cinny

* **Tarih:** 15 Mart 2026
* **Durum:** ✅ Kabul Edildi — Aktif
* **Bağlam:** Proje geliştirme sürecinde yürütülen kapsamlı araştırma ve mimari değerlendirme sonucunda Stoat Chat'in projenin güvenlik birinci prensibini karşılamadığı tespiti yapılmıştır. Stoat Chat'te E2EE varsayılan olarak bulunmamakta; eklenmesi tek geliştirici için ayrı bir proje niteliğinde iş yükü oluşturmaktadır. Oysa projenin özü güvenlik icat etmek değil, güvenli bir platform üzerine Pardus'a özgü değer katmaktır.
* **Karar:** Temel platform Stoat Chat'ten Matrix protokolü + Cinny istemcisi kombinasyonuna taşınmaktadır. 
  * **İstemci:** Cinny (cinnyapp/cinny) — TypeScript/React, fork alınacak
  * **Masaüstü:** Cinny Desktop (cinnyapp/cinny-desktop) — Tauri, fork alınacak
  * **Homeserver:** Synapse — Docker Compose ile kurulum
  * **Ses/Video:** LiveKit SFU + lk-jwt-service + Element Call widget
  * **Veritabanı:** PostgreSQL (Synapse'in zorunlu kıldığı)
* **Gerekçe:**
  1. **Güvenlik miras alınır, icat edilmez:** Matrix'in Olm/Megolm şifreleme katmanı bağımsız denetimden geçmiş, NATO ve 35'ten fazla ülke hükümeti tarafından üretimde kullanılmaktadır. Bu güvenlik Neo'ya miras yoluyla geçer.
  2. **E2EE varsayılan:** Stoat Chat'te sıfırdan implement edilmesi gereken E2EE, Matrix'te protokolün ta kendisidir.
  3. **Markalaştırma kolaylığı:** Cinny, `config.json` ve CSS değişkenleriyle markalaştırılabilecek sade bir kod tabanına sahiptir.
  4. **Tauri avantajı:** Cinny Desktop, Electron yerine Tauri kullanmaktadır. Bu; daha küçük paket boyutu, daha düşük bellek tüketimi ve daha güçlü güvenlik mimarisi demektir. Tauri otomatik olarak `.deb` paketi üretir.
  5. **Aktif geliştirme:** Cinny v4.10.5 (Şubat 2026), 78 katkıcı, 3.4k yıldız, **0 açık güvenlik bildirimi**.
  6. **Teknofest argümanı:** "NATO ve 35 ülke hükümetinin güvendiği Matrix protokolü üzerine inşa edilmiştir" ifadesi projenin güvenlik iddiasını güçlü referanslarla destekler.
* **Sonuçlar:**
  * (+) Güvenlik katmanı temelden sağlanmış, geliştirici zamanı Pardus entegrasyonuna odaklanabilir
  * (+) `.deb` paketi Tauri ile otomatik üretiliyor
  * (+) 0 güvenlik açığı ile başlanıyor
  * (+) 1.5 aylık ek süre bu geçişi rahat karşılıyor
  * (-) Synapse Python tabanlı, i5-2. nesil sunucuda kaynak kullanımı izlenecek
  * (-) Cinny'de grup ses/video Element Call ile sağlanıyor; entegrasyon gerektiriyor
  ***

### ADR-006 — Masaüstü Teknolojisi : Tauri (Electron yerine)

* **Tarih:** 15 Mart 2026
* **Durum:** ✅ Kabul Edildi — ADR-005'in alt kararı
* **Bağlam:** Cinny Desktop'un Tauri ile yazılmış olması, Electron'a kıyasla önemli avantajlar sunmaktadır.
* **Karar:** Masaüstü uygulaması Tauri tabanlı Cinny Desktop fork'u üzerinden geliştirilecektir.
* **Sonuçlar:**
  * Uygulama boyutu Electron'a kıyasla 5-10x küçük
  * Bellek tüketimi önemli ölçüde düşük
  * Rust güvenlik mimarisi (sandbox, IPC kısıtlamaları)
  * `npm run tauri build` komutu doğrudan `.deb` üretiyor
  * Hedef: Pardus 25 GNOME ve XFCE'de sorunsuz çalışan, yerel görünümlü uygulama

***

### ADR-007 — Veritabanı : PostgreSQL

* **Tarih:** 15 Mart 2026
* **Durum:** ✅ Kabul Edildi — ADR-005'in alt kararı
* **Bağlam:** Synapse, production ortamında PostgreSQL gerektirmektedir. SQLite yalnızca geliştirme ortamı için uygundur.
* **Karar:** Veritabanı olarak PostgreSQL kullanılacak; Docker iç ağında çalışacak, dışa hiçbir port açılmayacaktır.
* **Sonuçlar:** Güvenli izolasyon, Synapse ile tam uyumluluk, olgun ve stabil altyapı. HDD üzerinde I/O performansı izlenecek.

***

# KISIM F - Değişiklik Günlüğü

***

### 4 Mart 2026 

* Dokümantasyon tamamlandı 
* Stoat Chat kaynak kodları indirildi, dosya dizinleri ayarlandı : 

```
ozturu68@fedora:~/Projeler/TEKNOFEST/Pardus/Pardus-Akis$ ls -l
toplam 0
drwxr-xr-x. 1 ozturu68 ozturu68 222 Mar  4 20:48 auth
drwxr-xr-x. 1 ozturu68 ozturu68 638 Mar  4 20:48 backend
drwxr-xr-x. 1 ozturu68 ozturu68 848 Mar  4 20:48 desktop
drwxr-xr-x. 1 ozturu68 ozturu68 256 Mar  4 20:48 sdk
drwxr-xr-x. 1 ozturu68 ozturu68 200 Mar  4 20:48 self-hosted
drwxr-xr-x. 1 ozturu68 ozturu68 638 Mar  4 20:48 web
drwxr-xr-x. 1 ozturu68 ozturu68 480 Mar  4 20:48 web-legacy
ozturu68@fedora:~/Projeler/TEKNOFEST/Pardus/Pardus-Akis$ 
```

* Github reposu ayarlandı : 

***

### 15 Mart 2026

* **KÖKLÜ PLATFORM DEĞİŞİKLİĞİ — ADR-005**
* Stoat Chat kod tabanı devre dışı bırakıldı; ilgili klasörler arşivlendi
* Yeni temel: Matrix protokolü + Cinny istemcisi + Synapse homeserver
* Tauri masaüstü teknolojisi benimsendi (ADR-006)
* PostgreSQL veritabanı kararı alındı (ADR-007)
* Proje dokümantasyonu v2.0.0 olarak baştan yazıldı: 
  * KISIM A — Proje Tanımı: Vizyon, misyon ve teknik kimlik güncellendi
  * KISIM B — Gereksinimler: Bileşen karşılıkları eklendi, F8 (ekran paylaşımı) yeni gereksinim olarak eklendi
  * KISIM C — Mimari ve Teknik Temel: Tüm mimari Matrix ekosistemi üzerine yeniden yazıldı
  * KISIM D — Proje Yönetimi: Milestone yapısı ve deadline (15 Mayıs 2026) güncellendi
  * KISIM E — Karar Günlüğü: ADR-001 geçersiz kılındı; ADR-005, ADR-006, ADR-007 eklendi
  * KISIM F — Değişiklik Günlüğü: Bu kayıt

***

### 18 Mart 2026

**Milestone 1 tamamlandı — Analiz ve Ortam Hazırlığı**

* Ubuntu Server 24.04.4 LTS sanal makineye kuruldu (KVM/QEMU)
* Docker ve Docker Compose kurulumu tamamlandı
* Nginx kuruldu ve yapılandırıldı: 4 subdomain için reverse proxy ayarları yapıldı
* Cloudflare Tunnel kuruldu, `pardus-akis` tüneli oluşturuldu, 4 route eklendi:
  &#x20; \* `matrix.ozturu.com` → Synapse :8008
  &#x20; \* `app.ozturu.com` → Cinny :8080
  &#x20; \* `element.ozturu.com` → Element Call :8081
  &#x20; \* `rtc.ozturu.com` → LiveKit :7880
* UFW, fail2ban ve SSH yapılandırması tamamlandı
* PostgreSQL 17 container kuruldu, healthy durumu doğrulandı
* Synapse 1.149.1 container kuruldu, PostgreSQL'e bağlantı sağlandı
* `matrix.ozturu.com` üzerinden Matrix API erişimi doğrulandı (HTTPS)
* Admin kullanıcısı oluşturuldu

**Teknik notlar:**

* YAML'da özel karakter içeren şifreler `psycopg2` bağlantısında hata üretir — şifrelerde `^`, `#`, `~` gibi karakterlerden kaçınılmalı
* PostgreSQL data dizini sıfırlanmadan şifre değişikliği etkisiz kalır
* Fiziksel sunucu donanım güçlendirmesi yapılana kadar sanal makine ile devam edilmektedir

***
