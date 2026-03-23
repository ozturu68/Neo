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



