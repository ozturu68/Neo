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
