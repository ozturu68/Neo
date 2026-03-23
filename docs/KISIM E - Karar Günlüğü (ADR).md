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
