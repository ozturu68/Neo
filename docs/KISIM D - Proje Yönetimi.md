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

