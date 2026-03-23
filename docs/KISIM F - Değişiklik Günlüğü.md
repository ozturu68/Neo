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
