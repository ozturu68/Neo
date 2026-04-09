<div align="center">

<img src="shift-theory-logo.png" alt="Shift Theory" width="180" />

<br/>
<br/>

<img src="Neo-logo.png" alt="Neo" width="120" />

# Neo

**Fedora, Debian ve Pardus için Güvenli İletişim Platformu**

[![License: AGPL-3.0](https://img.shields.io/badge/Lisans-AGPL--3.0-blue.svg?style=flat-square)](LICENSE)
[![Matrix Protocol](https://img.shields.io/badge/Protokol-Matrix-00AEEF.svg?style=flat-square)](https://matrix.org)
[![Tauri v2](https://img.shields.io/badge/Framework-Tauri%20v2-FFC131.svg?style=flat-square)](https://tauri.app)
[![React 19](https://img.shields.io/badge/UI-React%2019-61DAFB.svg?style=flat-square)](https://react.dev)
[![TypeScript](https://img.shields.io/badge/Dil-TypeScript-3178C6.svg?style=flat-square)](https://www.typescriptlang.org)
[![Teknofest 2026](https://img.shields.io/badge/Teknofest-2026%20%E2%98%85-E30613.svg?style=flat-square)](https://teknofest.org)

<br/>

> *"Güvenlik birinci prensip, son adım değil."*

<br/>

[Özellikler](#-özellikler) · [Mimari](#-mimari) · [Kurulum](#-kurulum) · [Geliştirme](#-geliştirme) · [Güvenlik](#-güvenlik) · [Katkı](#-katkıda-bulunma)

</div>

---

## Proje Hakkında

**Neo**, Türkiye'nin millî işletim sistemi Pardus başta olmak üzere Fedora ve Debian platformları için **sıfırdan tasarlanmış**, açık kaynaklı, uçtan uca şifreli bir masaüstü iletişim platformudur.

Mevcut iletişim araçlarının büyük çoğunluğu verilerinizi yabancı sunucularda işler; yüksek kaynak tüketen Electron tabanlı mimariler üzerinde çalışır; ya da Türkçe kullanıcı deneyimi sunmaz. Neo bu üç sorunu aynı anda çözmek için geliştirildi.

### Neden Neo?

| Sorun | Diğer Araçlar | Neo |
|---|---|---|
| **Veri egemenliği** | Yabancı sunucular | Türkiye'deki fiziksel sunucu |
| **Şifreleme** | Opsiyonel veya yoktur | E2EE varsayılan, kapatamazsınız |
| **Kaynak tüketimi** | 300–500 MB RAM (Electron) | < 120 MB RAM hedefi (Tauri) |
| **Platform uyumu** | Çoğu Fedora/Debian/Pardus'ta sorunlu | Fedora, Debian ve Pardus için tasarlandı |
| **Kaynak kodu** | Kapalı | AGPL-3.0, tamamen açık |

---

## ✨ Özellikler

### 🔐 Güvenlik ve Gizlilik
- **Uçtan Uca Şifreleme (E2EE)** — Matrix'in bağımsız denetimden geçmiş Olm/Megolm şifreleme katmanı. NATO ve 35+ ülke hükümeti tarafından üretimde kullanılan şifreleme standardı.
- **E2EE Varsayılan Aktif** — Tüm özel mesajlar ve grup odaları şifreli oluşturulur; kullanıcı kapatamaz.
- **Cihaz Doğrulama** — QR kod veya emoji karşılaştırması ile cihaz doğrulama (cross-signing).
- **Güvenli Token Saklama** — Oturum jetonları sistem keyring'inde saklanır; tarayıcı deposunda değil.

### 💬 Mesajlaşma
- Gerçek zamanlı özel ve grup mesajlaşması
- Dosya paylaşımı (resim, video, belge, ses)
- Mesaj düzenleme ve silme
- Emoji reaksiyonları
- Yazıyor... göstergesi ve okundu bildirimleri

### 📞 Ses ve Görüntü
- 1:1 ve grup sesli görüşme
- 1:1 ve grup görüntülü görüşme
- Ekran paylaşımı (Wayland PipeWire + X11 desteği)
- LiveKit SFU altyapısı üzerinden WebRTC

### 🖥️ Platform Entegrasyonu
- Sistem tepsisi (tray) entegrasyonu
- Masaüstü bildirimleri (libnotify)
- `.desktop` dosyası ile uygulama menüsü entegrasyonu
- Fedora/Debian/Pardus GNOME, XFCE ve KDE Plasma uyumluluğu
- `.deb` ve `.rpm` paket desteği

### 🌍 Yerelleştirme
- Tam Türkçe arayüz (birincil)
- İngilizce dil desteği (ikincil / yedek)
- i18next altyapısı — yeni dil eklemek kolaylaştırılmıştır

---

## 🏗️ Mimari

Neo, 6 katmanlı bir güvenlik ve uygulama mimarisine sahiptir:

```
┌─────────────────────────────────────────────────────────────────────┐
│  KATMAN 6: Fedora / Debian / Pardus UI Markalaşması & Test         │
│  Pardus renk paleti · i18n · Vitest + React Testing Library        │
├─────────────────────────────────────────────────────────────────────┤
│  KATMAN 5: UI Bileşenleri & Chat Akışı                             │
│  LoginScreen · RoomList · MessageBubble · MessageInput             │
├─────────────────────────────────────────────────────────────────────┤
│  KATMAN 4: State Yönetimi & Sync                                   │
│  Zustand stores: auth · rooms · messages · ui                      │
├─────────────────────────────────────────────────────────────────────┤
│  KATMAN 3: Matrix SDK Wrapper & E2EE                               │
│  matrix-js-sdk v41 · Olm/Megolm · type-safe wrappers              │
├─────────────────────────────────────────────────────────────────────┤
│  KATMAN 2: Tauri IPC & Güvenli Depolama                            │
│  Rust komutları · keyring token · CSP yapılandırması               │
├─────────────────────────────────────────────────────────────────────┤
│  KATMAN 1: Sunucu Altyapısı & DevOps                               │
│  Synapse · PostgreSQL · LiveKit · Cloudflare Tunnel                │
└─────────────────────────────────────────────────────────────────────┘
```

### Teknoloji Yığını

| Katman | Teknoloji | Açıklama |
|---|---|---|
| **Masaüstü Çerçeve** | Tauri v2 (Rust) | Native WebView, sandbox mimarisi |
| **UI** | React 19 + TypeScript | Strict mode, functional bileşenler |
| **Matrix SDK** | matrix-js-sdk v41.3 | E2EE, sync, media, VoIP sinyalizasyonu |
| **Stil** | Tailwind CSS v4 | Pardus renk değişkenleri, utility-first |
| **State** | Zustand v5 | Persist middleware ile persist |
| **i18n** | i18next + react-i18next | Türkçe birincil, İngilizce fallback |
| **Test** | Vitest + Testing Library | %80+ kapsam hedefi |
| **Homeserver** | Synapse v1.149 | PostgreSQL 17, Docker Compose |
| **Ses/Video** | LiveKit SFU + Element Call | JWT köprüsü, TURN/TLS |
| **Güvenlik** | UFW · fail2ban · Cloudflare | 6 katmanlı güvenlik modeli |

### Proje Dizin Yapısı

```
neo/
├── src/
│   ├── components/
│   │   ├── auth/          # LoginScreen
│   │   ├── chat/          # MessageBubble, MessageList
│   │   ├── layout/        # Sidebar, MainPanel, RightPanel
│   │   └── rooms/         # RoomList
│   ├── lib/
│   │   ├── matrix/        # SDK wrapper katmanı
│   │   │   ├── client.ts  # MatrixClient singleton
│   │   │   ├── auth.ts    # Giriş / oturum yönetimi
│   │   │   ├── rooms.ts   # Oda CRUD
│   │   │   ├── messages.ts# Mesaj gönderme, düzenleme
│   │   │   ├── crypto.ts  # E2EE yardımcıları
│   │   │   └── media.ts   # Dosya yükleme (50 MB limit)
│   │   ├── store/         # Zustand state store'ları
│   │   ├── storage/       # Platform soyutlama katmanı
│   │   ├── config/        # Ortam yapılandırması
│   │   ├── errors/        # Tip hiyerarşisi + i18n hata mesajları
│   │   └── i18n/          # Çeviri dosyaları (tr/en)
│   ├── styles/
│   │   └── globals.css    # Pardus CSS değişkenleri + Tailwind
│   └── types/
│       └── matrix.ts      # Matrix event tip tanımları
├── src-tauri/
│   └── src/
│       └── commands/
│           ├── auth.rs        # Keyring token yönetimi
│           ├── notifications.rs
│           └── system.rs
└── ...
```

---

## 🖥️ Sistem Gereksinimleri

### Geliştirme Ortamı

| Gereksinim | Minimum Sürüm |
|---|---|
| Node.js | 20 LTS |
| Rust | 1.70+ |
| npm | 8+ |

### Linux Sistem Kütüphaneleri

**Debian 13 / Ubuntu 24.04 / Pardus 25:**
```bash
sudo apt install -y \
  pkg-config \
  libwebkit2gtk-4.1-dev \
  libgtk-3-dev \
  libayatana-appindicator3-dev \
  librsvg2-dev \
  clang \
  libssl-dev \
  libxkbcommon-dev \
  libdbus-1-dev
```

**Fedora 42:**
```bash
sudo dnf install -y \
  pkg-config \
  webkit2gtk4.1-devel \
  gtk3-devel \
  libappindicator-gtk3-devel \
  librsvg2-devel \
  clang \
  openssl-devel \
  libxkbcommon-devel \
  dbus-devel
```

---

## 🚀 Kurulum

### Üretim Paketi (Tavsiye Edilen)

```bash
# Debian / Ubuntu / Pardus
sudo apt install ./neo_0.1.0_amd64.deb

# Fedora
sudo dnf install ./neo-0.1.0-1.x86_64.rpm
```

### Kaynaktan Derleme

```bash
# 1. Rust kurulumu
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source "$HOME/.cargo/env"

# 2. Repoyu klonlayın
git clone https://github.com/ozturu68/NEO.git
cd NEO

# 3. Bağımlılıkları yükleyin
npm install

# 4. Derleme doğrulaması
cd src-tauri && cargo build && cd ..
```

---

## 🛠️ Geliştirme

### Geliştirme Sunucusu

```bash
# Yalnızca frontend (Vite hot-reload)
npm run dev

# Tam Tauri + React geliştirme ortamı (önerilen)
npm run tauri dev
```

### Kalite Kontrol

```bash
# TypeScript tip kontrolü
npm run type-check

# ESLint denetimi
npm run lint

# Linting + auto-fix
npm run lint:fix

# Test suite
npm run test

# Test (watch modu)
npm run test:watch

# Kapsam raporu
npm run test:coverage

# Tüm kontroller (CI eşdeğeri)
npm run validate
```

### Üretim Paketi Derleme

```bash
# .deb paketi (Debian/Pardus)
npm run tauri build -- --bundles deb

# .rpm paketi (Fedora)
npm run tauri build -- --bundles rpm
```

Çıktı: `src-tauri/target/release/bundle/`

---

## 🧪 Test Stratejisi

Neo üç katmanlı bir test yaklaşımı benimser:

### Kapsam Hedefleri

| Modül Grubu | Hedef |
|---|---|
| Kritik (auth · crypto · messages) | ≥ %80 |
| UI bileşenleri | ≥ %60 |
| Utility fonksiyonlar | ≥ %90 |

### Test Çalıştırma

```bash
# Yalnızca Matrix wrapper testleri
npm run test -- src/lib/matrix/

# Yalnızca bileşen testleri
npm run test -- src/components/

# HTML kapsam raporu
npm run test:coverage
# Raporu açmak için: open coverage/index.html
```

### Mocking Yaklaşımı

Matrix SDK doğrudan test edilmez; `vi.mock('./client')` ile `getMatrixClient` taklit edilir:

```typescript
vi.mock('./client', () => ({
  getMatrixClient: vi.fn(() => ({
    sendEvent: vi.fn().mockResolvedValue({ event_id: '$test' }),
  })),
}));
```

---

## 🔒 Güvenlik

Neo, 6 katmanlı bir güvenlik mimarisine sahiptir:

```
KATMAN 1 — Ağ Güvenliği
  TLS 1.3 zorunlu · HSTS · CSP · DDoS (Cloudflare) · UFW

KATMAN 2 — Sunucu Sertleştirme
  fail2ban · Docker iç ağ izolasyonu · Otomatik güvenlik güncellemeleri

KATMAN 3 — Kimlik Doğrulama
  Synapse kayıt kapalı · Rate limiting · Güçlü şifre politikası

KATMAN 4 — Veri Güvenliği
  E2EE varsayılan (Olm/Megolm) · PostgreSQL iç ağda · Medya kısıtlamaları

KATMAN 5 — Uygulama Güvenliği
  Tauri CSP · IPC whitelist · Input validation · XSS koruması

KATMAN 6 — İzleme & Yanıt
  Structured logging · fail2ban · Incident response planı
```

### Güvenlik Açığı Bildirimi

Güvenlik açıklarını GitHub Issues üzerinden **değil**, doğrudan aşağıdaki adrese bildirin:

📧 `m.umut.ozturk@protonmail.com` — Konu: `[NEO SECURITY]`

Bildiriminiz 24 saat içinde teyit edilir, 30 gün içinde yama yayınlanır.

---

## 🌐 Sunucu Altyapısı

### Domain Yapısı

| Subdomain | Hedef | Açıklama |
|---|---|---|
| `matrix.ozturu.com` | Synapse :8008 | Matrix homeserver API |
| `app.ozturu.com` | Frontend :8080 | Web istemcisi |
| `element.ozturu.com` | Element Call :8081 | Ses/video widget |
| `rtc.ozturu.com` | LiveKit :7880 | WebRTC SFU + JWT |

Tüm bağlantılar **Cloudflare Tunnel** üzerinden yönlendirilir; sunucuda doğrudan port açılmamıştır.

### Sunucu Özellikleri

| Donanım | Yazılım |
|---|---|
| Intel Core i5 (2. Nesil) | Ubuntu Server 24.04 LTS |
| 16 GB RAM | Docker + Docker Compose |
| 300 GB HDD | Synapse v1.149 + PostgreSQL 17 |

---

## 🤝 Katkıda Bulunma

Neo açık kaynaklı bir projedir; katkılarınızı bekliyoruz.

### Katkı Adımları

1. Bu repoyu **fork** edin
2. Feature branch oluşturun: `git checkout -b feature/harika-ozellik`
3. Değişikliklerinizi yapın ve test edin: `npm run validate`
4. Commit edin (Conventional Commits formatı):
   ```
   feat(rooms): E2EE varsayılan oda oluşturma eklendi
   fix(auth): Token yenileme hatası giderildi
   docs(readme): Kurulum kılavuzu güncellendi
   ```
5. Push edin: `git push origin feature/harika-ozellik`
6. **Pull Request** açın

### Katkı Kuralları

- Kod stil kurallarına uyun (`.kilo/rules/code-style.md`)
- Yeni özellikler için test yazın
- Güvenlik önceliğini koruyun — E2EE hiçbir zaman bypass edilemez
- Hata mesajları ve yorumlar Türkçe yazılabilir
- `matrix-js-sdk` doğrudan bileşenlerde kullanılmaz; `src/lib/matrix/` wrapper katmanı kullanılır

### Kapsam Dışı (Bu Sürüm)

- Mobil uygulama (Android/iOS)
- Matrix federasyon ve çoklu homeserver
- Thread / Spaces tam desteği
- Bot API
- E2EE sesli/görüntülü (MatrixRTC olgunlaşınca)

---

## 📍 Yol Haritası

| Milestone | Durum | Açıklama |
|---|---|---|
| M0 — Zemin Hazırlığı | ✅ Tamamlandı | Dokümantasyon, repo kurulumu |
| M1 — Sunucu Altyapısı | ✅ Tamamlandı | Synapse + PostgreSQL + Cloudflare |
| M2 — İstemci İskeleti | 🔄 Aktif (~%70) | Tauri + React + Matrix SDK |
| M3 — Temel Mesajlaşma | ⏳ Sırada | Oda listesi, chat, dosya paylaşımı |
| M4 — Ses/Video | ⏳ Sırada | LiveKit + Element Call entegrasyonu |
| M5 — Güvenlik Sertleştirme | ⏳ Sırada | Tam güvenlik katmanları + yük testi |
| M6 — Pardus Markalaşması | ⏳ Sırada | Görsel kimlik, .deb/.rpm paketleme |
| M7 — Sunum Hazırlığı | ⏳ Sırada | Demo videosu, Teknofest sunumu |

**Hedef deadline:** 15 Mayıs 2026 — Teknofest 2026

---

## 📄 Lisans

Neo, **GNU Affero General Public License v3.0** (AGPL-3.0) altında lisanslanmıştır.

```
Copyright (C) 2026  Shift Theory Takımı

Bu program özgür yazılımdır: GNU Affero Genel Kamu Lisansı'nın 3. sürümü veya
(isteğinize bağlı olarak) daha sonraki bir sürümün koşulları altında
yeniden dağıtabilir ve/veya değiştirebilirsiniz.

Bu program, yararlı olması umuduyla dağıtılmakta olup, hiçbir garanti
verilmemektedir. Ayrıntılar için AGPL-3.0 lisansına bakın.
```

---

## 👤 İletişim

| | |
|---|---|
| **Geliştirici** | Muzaffer Umut Öztürk |
| **Takım** | Shift Theory |
| **GitHub** | [@ozturu68](https://github.com/ozturu68) |
| **E-posta** | m.umut.ozturk@protonmail.com |
| **Matrix** | @ozturu68:matrix.ozturu.com |
| **Proje URL** | https://github.com/ozturu68/NEO |

---

<div align="center">

<br/>

<img src="shift-theory-logo.png" alt="Shift Theory" width="100" />

<br/>

**Shift Theory Takımı** tarafından 🇹🇷 ile geliştirildi

*Teknofest 2026 — Pardus Hata Yakalama ve Öneri Yarışması*

<br/>

[![Repo'yu Yıldızla](https://img.shields.io/github/stars/ozturu68/NEO?style=social)](https://github.com/ozturu68/NEO)

</div>