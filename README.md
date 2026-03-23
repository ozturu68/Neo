# 🛡️ Neo: Pardus İçin Güvenli ve Yerli İletişim Platformu

[![Lisans: AGPL-3.0](https://img.shields.io/badge/Lisans-AGPL--3.0-blue.svg)](https://opensource.org/licenses/AGPL-3.0)
[![Platform: Pardus 25](https://img.shields.io/badge/Platform-Pardus%2025-red.svg)](https://www.pardus.org.tr/)
[![Protokol: Matrix](https://img.shields.io/badge/Protokol-Matrix-000000.svg?logo=matrix)](https://matrix.org/)
[![Teknoloji: Tauri](https://img.shields.io/badge/Teknoloji-Tauri-FFC131.svg?logo=tauri)](https://tauri.app/)

**Neo**, Türkiye'nin milli işletim sistemi **Pardus** ile derin entegrasyon içerisinde çalışan, uçtan uca şifreli (E2EE), açık kaynaklı ve merkezi bir iletişim platformudur. Teknofest 2026 kapsamında geliştirilen bu proje, kullanıcıların veri egemenliğini korurken modern bir iletişim deneyimi sunmayı hedefler.

---

## 🚀 Öne Çıkan Özellikler

*   **🔒 Tavizsiz Güvenlik:** Matrix protokolünün bağımsız denetimlerden geçmiş **Olm/Megolm** şifreleme altyapısı ile varsayılan olarak uçtan uca şifreli iletişim.
*   **📞 Kesintisiz İletişim:** LiveKit SFU altyapısı ile yüksek kaliteli sesli ve görüntülü görüşme, ekran paylaşımı desteği.
*   **🐧 Pardus Entegrasyonu:** Pardus 25 "Bilge" görsel kimliğiyle uyumlu arayüz, `.deb` paketi ile kolay kurulum ve masaüstü bildirim entegrasyonu.
*   **🇹🇷 Tam Yerlilik:** Verilerin Türkiye'deki fiziksel sunucularda barındırılması ve %100 Türkçe arayüz desteği.
*   **🏛️ Atatürk Köşesi:** Milli değerlerimizi yansıtan, uygulama içerisine entegre özel Atatürk köşesi bileşeni.

---

## 🛠️ Teknik Mimari

Neo, "güvenliği icat etmek yerine, kanıtlanmış güvenliği miras alma" felsefesiyle inşa edilmiştir.

### İstemci Tarafı (Neo Client)
*   **Temel:** [Cinny](https://github.com/cinnyapp/cinny) (Matrix İstemcisi) fork'u.
*   **Masaüstü Çerçevesi:** [Tauri](https://tauri.app/) (Rust tabanlı, hafif ve güvenli).
*   **Arayüz:** React + Pardus Renk Paleti + Özelleştirilmiş CSS.

### Sunucu Tarafı (Neo Backend)
*   **Homeserver:** [Synapse](https://github.com/element-hq/synapse) (Matrix referans sunucusu).
*   **Veritabanı:** PostgreSQL (Dockerize edilmiş, dış dünyaya kapalı).
*   **Medya/SFU:** LiveKit + Element Call entegrasyonu.
*   **Bağlantı:** Cloudflare Tunnel (Statik IP gerektirmeyen, güvenli tünelleme).

---

## 📦 Kurulum

### Pardus 25 Üzerinde Kurulum
Neo, Pardus kullanıcıları için hazır `.deb` paketi olarak sunulmaktadır.

```bash
# Depoyu klonlayın (veya sürüm sayfasından .deb dosyasını indirin)
wget https://github.com/kullanici/neo/releases/download/v2.0.0/neo-desktop_2.0.0_amd64.deb

# Paketi kurun
sudo apt install ./neo-desktop_2.0.0_amd64.deb
```

### Geliştirici Ortamı Hazırlığı
Projeyi kendi yerelinizde derlemek isterseniz:

1.  **Bağımlılıkları Kurun:** Rust, Node.js ve Tauri bağımlılıklarının sisteminizde yüklü olduğundan emin olun.
2.  **Repoyu Klonlayın:** `git clone https://github.com/kullanici/neo.git`
3.  **Bağımlılıkları Yükleyin:** `npm install`
4.  **Geliştirme Modunda Çalıştırın:** `npm run tauri dev`

---

## 🛡️ Güvenlik Katmanları

Neo'nun güvenlik mimarisi 6 temel katmandan oluşur:
1.  **Ağ:** TLS 1.3, HSTS ve Cloudflare DDoS koruması.
2.  **Sunucu:** Fail2ban, Nginx rate limiting ve UFW sertleştirme.
3.  **Kimlik:** Yalnızca davetle üyelik ve güçlü şifre politikaları.
4.  **Veri:** Varsayılan E2EE (Olm/Megolm) ve izole veritabanı.
5.  **Uygulama:** Düzenli bağımlılık taramaları (npm audit).
6.  **İzleme:** Docker log yönetimi ve düzenli PostgreSQL yedeklemeleri.

---

## 🗺️ Yol Haritası

- [x] **Milestone 0-1:** Altyapı kurulumu ve temel mesajlaşma.
- [ ] **Milestone 2-3:** Sesli/Görüntülü görüşme entegrasyonu ve güvenlik sertleştirmesi.
- [ ] **Milestone 4-5:** Pardus markalaştırması, Türkçe dil desteği ve Atatürk Köşesi.
- [ ] **Milestone 6-7:** Paketleme (.deb), performans testleri ve lansman.

---

## 🤝 Katkıda Bulunma

Neo, açık kaynak topluluğunun katkılarına açıktır.
1. Bu depoyu çatallayın (Fork).
2. Yeni bir özellik dalı oluşturun (`git checkout -b ozellik/yeniOzellik`).
3. Değişikliklerinizi kaydedin (`git commit -m 'Yeni özellik eklendi'`).
4. Dalınıza itin (`git push origin ozellik/yeniOzellik`).
5. Bir Çekme İsteği (Pull Request) oluşturun.

---

## 📄 Lisans

Bu proje **AGPL-3.0** lisansı ile lisanslanmıştır. Detaylar için [LICENSE](LICENSE) dosyasına göz atabilirsiniz.

---

## 👨‍💻 Geliştirici

*   **Muzaffer Umut Öztürk** - *Baş Geliştirici* - [GitHub](https://github.com/ozturu68)
*   **Ayşen Alçakır** - *Danışman Öğretmen*

---

> **Not:** Bu proje Teknofest 2026 "Pardus Hata Yakalama ve Öneri Yarışması" kapsamında geliştirilmektedir.
