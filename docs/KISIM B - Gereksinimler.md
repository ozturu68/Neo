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

