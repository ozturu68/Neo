<div align="center">

<img src="shift-theory-logo.png" alt="Shift Theory" width="180" />

<br/>
<br/>

<img src="Neo-logo.png" alt="NEO" width="120" />

# NEO

**Shift Theory takımı tarafından geliştirilen, Matrix tabanlı güvenli iletişim platformu**

[![License: AGPL-3.0](https://img.shields.io/badge/License-AGPL--3.0-blue.svg?style=flat-square)](LICENSE)
[![Protocol: Matrix](https://img.shields.io/badge/Protocol-Matrix-00AEEF.svg?style=flat-square)](https://matrix.org)
[![Desktop: Tauri v2](https://img.shields.io/badge/Desktop-Tauri%20v2-FFC131.svg?style=flat-square)](https://tauri.app)
[![UI: React 19](https://img.shields.io/badge/UI-React%2019-61DAFB.svg?style=flat-square)](https://react.dev)
[![Language: TypeScript](https://img.shields.io/badge/Language-TypeScript-3178C6.svg?style=flat-square)](https://www.typescriptlang.org)
[![CI](https://img.shields.io/github/actions/workflow/status/ozturu68/NEO/ci.yml?style=flat-square&label=CI)](https://github.com/ozturu68/NEO/actions/workflows/ci.yml)
[![Teknofest 2026](https://img.shields.io/badge/Teknofest-2026-E30613.svg?style=flat-square)](https://teknofest.org)

</div>

---

## İçindekiler

- [NEO Nedir?](#neo-nedir)
- [Neden NEO?](#neden-neo)
- [Proje Durumu](#proje-durumu)
- [Mimari Yaklaşım](#mimari-yaklaşım)
- [Teknoloji Yığını](#teknoloji-yığını)
- [Dizin Yapısı](#dizin-yapısı)
- [Logo Varlıkları](#logo-varlıkları)
- [Kurulum](#kurulum)
- [Geliştirme Komutları](#geliştirme-komutları)
- [Test ve Kalite](#test-ve-kalite)
- [Paketleme](#paketleme)
- [Güvenlik](#güvenlik)
- [CI/CD](#cicd)
- [Dokümantasyon Haritası](#dokümantasyon-haritası)
- [Yol Haritası](#yol-haritası)
- [Katkı](#katkı)
- [Lisans](#lisans)
- [Takım ve İletişim](#takım-ve-iletişim)

---

## NEO Nedir?

**NEO**, Teknofest 2026 bağlamında Shift Theory takımı tarafından geliştirilen, Fedora / Debian / Pardus odaklı açık kaynak bir masaüstü iletişim istemcisidir.

Proje; Matrix protokolünü, Tauri v2 + React + TypeScript istemci mimarisiyle birleştirir.

Ana hedefler:

- veri egemenliğini destekleyen, kontrol edilebilir bir iletişim altyapısı
- güvenliği sonradan eklenen değil, varsayılan davranış haline gelen bir tasarım
- Electron yerine Tauri ile düşük bellek tüketimi ve daha hafif dağıtım
- Pardus, Fedora ve Debian ekosistemleri için yerel masaüstü deneyimi

---

## Neden NEO?

| Başlık | Klasik yaklaşım | NEO yaklaşımı |
|---|---|---|
| Veri konumu | Çoğunlukla yabancı servisler | Matrix tabanlı, yönetilebilir altyapı |
| Şifreleme | Çoğu üründe opsiyonel | E2EE varsayılan odak |
| Masaüstü mimarisi | Genellikle Electron | Tauri v2 (Rust + native WebView) |
| Linux odağı | Dağıtım bağımsız genel yaklaşım | Fedora / Debian / Pardus öncelikli |
| Kod sahipliği | Kısıtlı veya kapalı kaynak | AGPL-3.0 açık kaynak |

---

## Proje Durumu

> Güncel durum: Milestone 2 aktif (~%70), istemci çekirdeği çalışır, özellikler kademeli olarak tamamlanıyor.

| Alan | Durum |
|---|---|
| İstemci altyapısı | Tauri + React + TypeScript kurulu |
| Matrix wrapper katmanı | `auth`, `rooms`, `messages`, `media`, `crypto`, `sync` mevcut |
| Tauri backend komutları | `auth`, `notifications`, `system` mevcut |
| Test altyapısı | Vitest + React Testing Library aktif |
| CI hattı | lint + type-check + test + build aktif |

### Çalışan ana parçalar

- Matrix şifreli giriş akışı (`src/lib/matrix/client.ts`, `src/lib/matrix/auth.ts`)
- Oturum token saklama soyutlaması (web localStorage + Tauri keyring)
- Oda listesi / aktif oda / mesaj store iskeleti
- Oda oluşturma sırasında varsayılan E2EE state (Megolm)
- Mesaj gönderme, düzenleme, redaction ve reaction wrapper fonksiyonları
- Medya yüklemede dosya boyutu ve MIME type doğrulaması

### Geliştirme aşamasında olan alanlar

- sohbet UX kapsamının olgunlaştırılması
- i18n kapsamının genişletilmesi
- VoIP entegrasyonu (`src/lib/matrix/voip.ts` TODO)

---

## Mimari Yaklaşım

NEO, katmanlı bir mimariyle geliştirilmektedir:

1. **Sunucu katmanı:** Synapse + PostgreSQL + LiveKit
2. **Tauri IPC katmanı:** Rust komutları + güvenli token depolama
3. **Matrix wrapper katmanı:** `src/lib/matrix/` altında type-safe servisler
4. **State katmanı:** Zustand store'ları (`auth`, `rooms`, `messages`, `ui`)
5. **UI katmanı:** React bileşenleri (`src/components/`)
6. **Destek katmanı:** i18n, tema, test, kalite süreçleri

Kritik mimari kural:

- `matrix-js-sdk` doğrudan React bileşenlerinde kullanılmaz
- tüm Matrix işlemleri wrapper katmanından yürütülür

---

## Teknoloji Yığını

| Katman | Teknoloji |
|---|---|
| Masaüstü | Tauri v2 |
| UI | React 19 |
| Dil | TypeScript 5 |
| Protokol SDK | matrix-js-sdk 41.3 |
| State yönetimi | Zustand 5 |
| Stil sistemi | Tailwind CSS v4 |
| i18n | i18next + react-i18next |
| Test | Vitest + Testing Library |
| Lint | ESLint + typescript-eslint |
| Rust tarafı | Tauri command modülleri + keyring |

---

## Dizin Yapısı

```text
NEO/
├── src/
│   ├── components/          # auth, chat, layout, rooms, ...
│   ├── lib/
│   │   ├── matrix/          # Matrix wrapper katmanı
│   │   ├── store/           # Zustand store'ları
│   │   ├── storage/         # Tauri/web storage abstraction
│   │   ├── config/          # Merkezi konfigürasyon
│   │   ├── errors/          # Typed error modelleri
│   │   └── i18n/            # tr/en locale dosyaları
│   ├── styles/              # global stiller
│   └── types/               # Matrix tip tanımları
├── src-tauri/
│   ├── src/commands/        # Rust IPC komutları
│   ├── capabilities/        # capability policy dosyaları
│   └── tauri.conf.json      # Tauri uygulama ayarları
├── .github/workflows/       # CI pipeline
├── INSTALL.md               # kurulum rehberi
├── SECURITY.md              # güvenlik politikası
├── CONTRIBUTING.md          # katkı rehberi
└── README.md
```

---

## Logo Varlıkları

README içinde kullanılan logo dosyaları:

- Shift Theory logosu: `shift-theory-logo.png`
- NEO logosu: `Neo-logo.png`

Her iki dosya da proje kök dizininde (`README.md` ile aynı dizinde) konumlandırılmıştır.

---

## Kurulum

### 1) Linux sistem bağımlılıkları

**Debian 13 / Ubuntu 24.04 / Pardus 25**

```bash
sudo apt install -y \
  pkg-config \
  libwebkit2gtk-4.1-dev \
  libgtk-3-dev \
  libayatana-appindicator3-dev \
  librsvg2-dev \
  clang \
  libssl-dev \
  curl \
  libsoup-3.0-dev \
  libxkbcommon-dev \
  libdbus-1-dev
```

**Fedora 42+**

```bash
sudo dnf install -y \
  pkg-config \
  webkit2gtk4.1-devel \
  gtk3-devel \
  libappindicator-gtk3-devel \
  librsvg2-devel \
  clang \
  openssl-devel \
  curl \
  libsoup-devel \
  libxkbcommon-devel \
  dbus-devel
```

### 2) Sürüm gereksinimleri

- Node.js: `20+`
- npm: `8+`
- Rust: `1.70+`

Rust kurulu değilse:

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source "$HOME/.cargo/env"
```

### 3) Projeyi çalıştırma

```bash
git clone https://github.com/ozturu68/NEO.git
cd NEO
npm install
cargo tauri info
```

---

## Geliştirme Komutları

| Komut | Açıklama |
|---|---|
| `npm run dev` | Vite frontend geliştirme sunucusu |
| `npm run tauri dev` | Tauri + React tam geliştirme akışı |
| `npm run build` | Production frontend build |
| `npm run preview` | Build çıktısını önizleme |
| `npm run lint` | ESLint denetimi |
| `npm run lint:fix` | Otomatik lint düzeltmeleri |
| `npm run type-check` | TypeScript tip denetimi |
| `npm run test` | Vitest testleri |
| `npm run test:watch` | Watch modunda test |
| `npm run test:coverage` | Coverage raporu |
| `npm run validate` | lint + type-check + test zinciri |

---

## Test ve Kalite

Kalite güvence yaklaşımı:

- **Lint:** kod stili ve temel statik analiz
- **Type-check:** strict TypeScript denetimi
- **Unit test:** Matrix wrapper fonksiyonları
- **Component test:** React bileşen davranış testleri
- **CI doğrulaması:** tüm kontrollerin otomatik çalışması

Örnek test dosyaları:

- `src/lib/matrix/messages.test.ts`
- `src/lib/matrix/rooms.test.ts`
- `src/components/rooms/RoomList.test.tsx`

---

## Paketleme

Mevcut konfigürasyonda varsayılan bundle hedefi `.deb`:

```bash
npm run tauri build -- --bundles deb
```

Çıktı dizini:

```text
src-tauri/target/release/bundle/deb/
```

---

## Güvenlik

Proje, "default secure" yaklaşımını izler:

- token depolama Tauri tarafında system keyring üzerinden yapılır
- oda oluşturmada E2EE state varsayılan olarak eklenir
- medya yüklemede dosya boyutu + MIME type doğrulaması zorunludur
- Tauri CSP ile yalnızca izinli endpoint'lere erişim sağlanır
- IPC komutları explicit whitelist ile açılır

Güvenlik açığı bildirimi:

- E-posta: `m.umut.ozturk@protonmail.com`
- Konu satırı: `[NEO SECURITY]`
- Detay politika: `SECURITY.md`

---

## CI/CD

CI pipeline dosyası: `.github/workflows/ci.yml`

Pipeline adımları:

1. `npm ci`
2. `npm run lint`
3. `npm run type-check`
4. `npm run test`
5. `npm run build`
6. Tauri build doğrulaması

Tetikleyiciler:

- `main` ve `develop` branch push işlemleri
- `main` hedefli pull request işlemleri

---

## Dokümantasyon Haritası

- Kurulum: `INSTALL.md`
- Katkı: `CONTRIBUTING.md`
- Güvenlik: `SECURITY.md`
- Modüller: `MODULES.md`
- Ana proje dokümanı: `Proje_Ana_Dokümantasyonu.md`
- Mimari: `KISIM_C_-_Mimari_ve_Teknik_Temel.md`
- ADR kayıtları: `KISIM_E_-_Karar_Günlüğü__ADR_.md`
- Değişiklik günlüğü: `KISIM_F_-_Değişiklik_Günlüğü.md`

---

## Yol Haritası

| Milestone | Durum | Açıklama |
|---|---|---|
| M0 | Tamamlandı | Dokümantasyon ve başlangıç hazırlıkları |
| M1 | Tamamlandı | Synapse + PostgreSQL + sunucu altyapısı |
| M2 | Aktif | Tauri + React istemci çekirdeği |
| M3 | Sırada | Temel mesajlaşma ve oda akışı |
| M4 | Sırada | Sesli/görüntülü görüşme entegrasyonu |
| M5 | Sırada | Güvenlik sertleştirme + yük testleri |
| M6 | Sırada | Markalaşma + paketleme + dağıtım |
| M7 | Sırada | Sunum ve demo hazırlığı |

---

## Katkı

Katkı süreci için `CONTRIBUTING.md` rehberi esas alınır.

Kısa katkı kontrol listesi:

1. Değişiklik öncesi ilgili issue ile ilişkilendirme yap
2. Kod standartlarına uy
3. Yeni davranış için test ekle
4. PR öncesi `npm run validate` çalıştır

---

## Lisans

Bu proje **GNU Affero General Public License v3.0 (AGPL-3.0)** ile lisanslanmıştır.

Detaylar: `LICENSE`

---

## Takım ve İletişim

NEO programı **Shift Theory takımı** tarafından geliştirilmektedir.

| Alan | Bilgi |
|---|---|
| Takım | Shift Theory |
| Proje | NEO |
| Geliştirici | Muzaffer Umut Öztürk |
| GitHub | [@ozturu68](https://github.com/ozturu68) |
| E-posta | m.umut.ozturk@protonmail.com |
| Matrix | @ozturu68:matrix.ozturu.com |

<div align="center">

<img src="shift-theory-logo.png" alt="Shift Theory" width="96" />

<br/>

**Shift Theory Team**

</div>
