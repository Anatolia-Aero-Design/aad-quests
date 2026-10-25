# 🐧 Linux Temel Eğitimi

> [!abstract] **Amaç**
> Linux terminalini kullanabilmek, dosya sistemini tanımak ve yazılım geliştirme sürecinde ihtiyaç duyulacak temel Linux becerilerini kazanmak.

> [!warning] **Kurallar**
> - Görevleri mümkün olduğunca sadece terminal üzerinden tamamlayın.
> - Bilmediğiniz komutları ve kavramları araştırın.
> - Kullandığınız komutların ne işe yaradığını anlamaya çalışın.
> - Önemli dosyaları silmeden veya sistem ayarlarını değiştirmeden önce komutlarınızın etkisini araştırın.
> - Yapay zekaya doğrudan görevi yaptırmak yasaktır; sadece konuyu öğrenmek amaçlı kullanılabilir.
> - Görevleri yapıp geçmeye değil, komutları ve mantıklarını öğrenmeye odaklanın.

---

## 🧭 Görev 1: Terminalde Gezinme
Terminali açın ve sisteminizdeki dosya ve klasörleri keşfedin.

### Yapılacaklar
- [ ] Hangi kullanıcı olduğunuzu öğrenin.
- [ ] Hangi dizinde bulunduğunuzu öğrenin.
- [ ] Bulunduğunuz dizindeki dosya ve klasörleri listeleyin.
- [ ] Bir klasöre girin ve tekrar bir üst dizine dönün.
- [ ] Bulunduğunuz dizinin mutlak yolunu öğrenin.

> [!info] **Araştırılacak Konular**
> `whoami`, `pwd`, `ls`, `cd`, `mkdir`, mutlak ve göreli yollar, Linux terminali, gizli dosyalar.

---

## 📝 Görev 2: Dosya Oluşturma ve Düzenleme
Bir proje klasörü oluşturun ve içerisinde temel dosya işlemlerini gerçekleştirin.

### Yapılacaklar
- [ ] `linux-egitimi` adında bir klasör oluşturun.
- [ ] Klasör içinde `notlar.txt` ve `komutlar.txt` dosyalarını oluşturun.
- [ ] `nano` veya `vim` kullanarak `notlar.txt` dosyasına kendiniz hakkında birkaç satır yazın *(ikisiyle de denemeniz önerilir)*.
- [ ] Dosyanın içeriğini terminalde görüntüleyin.
- [ ] Terminalden komut kullanarak dosyaya yeni bir satır ekleyin.
- [ ] Dosyanın bir kopyasını oluşturun ve kopyanın adını değiştirin.
- [ ] Gereksiz dosyayı (kopyayı) silin.

> [!info] **Araştırılacak Konular**
> `touch`, `cat`, `echo`, `cp`, `mv`, `rm`, `nano`, `vim`, dosya oluşturma ve düzenleme teknikleri.

---

## 🗂️ Görev 3: Linux Dosya Sistemi
Linux dosya sisteminin hiyerarşik yapısını araştırın.

### Yapılacaklar
- [ ] Kök dizin (`/`) altında hangi dizinlerin bulunduğunu inceleyin.
- [ ] `/home`, `/etc`, `/tmp`, `/usr`, `/var` ve `/bin` dizinlerinin amaçlarını araştırın.
- [ ] Kendi kullanıcı ev dizininizin yolunu bulun.
- [ ] Sistemdeki geçici dosyaların nerede tutulduğunu öğrenin.
- [ ] Sistemdeki disk bölümlerini ve bağlı dosya sistemlerini listeleyin.

> [!info] **Araştırılacak Konular**
> Linux dosya sistemi hiyerarşisi (FHS), `/`, `/home`, `/etc`, `/tmp`, `/usr`, `/var`, `/bin`, `~`, `df`, `du`, `lsblk`.

---

## 🔍 Görev 4: Dosya Arama ve Çıktı Filtreleme
Bir dosyanın yerini bulmayı ve terminaldeki çıktıları filtrelemeyi öğrenin.

### Yapılacaklar
- [ ] Oluşturduğunuz `notlar.txt` dosyasını terminal üzerinden arayın.
- [ ] Bir dizindeki `.txt` uzantılı dosyaları listeleyin.
- [ ] Bir dosyanın içinde belirlediğiniz bir kelimeyi arayın.
- [ ] Bir komutun çıktısında yalnızca istediğiniz satırları gösterin.
- [ ] Bir komutun çıktısını başka bir dosyaya kaydedin.
- [ ] Bir komutun çıktısını ikinci bir komuta aktararak filtreleyin.

> [!tip] **Ek Görev**
> Sisteminizdeki `.conf` uzantılı dosyaları araştırın. Erişim izniniz olan bir dizinde bu dosyalardan birkaçını bulun ve ne amaçla kullanıldıklarını inceleyin.

> [!info] **Araştırılacak Konular**
> `find`, `grep`, `locate`, `which`, `whereis`, `head`, `tail`, `sort`, `wc`, `cut`, pipe (`|`), çıktı yönlendirme (`>`, `>>`).

---

## 🔒 Görev 5: Dosya İzinleri ve Kullanıcılar
Linux'ta dosyalara erişimin nasıl kontrol edildiğini öğrenin.

### Yapılacaklar
- [ ] Kendi oluşturduğunuz bir dosyanın izinlerini görüntüleyin.
- [ ] Dosyanın sahibi ve grubunun kim olduğunu öğrenin.
- [ ] Dosyanın izinlerini değiştirin.
- [ ] Bir dosyaya yalnızca sahibi tarafından yazılabilecek izinler verin.
- [ ] Sayısal (oktal) ve sembolik izin gösterimleri arasındaki farkı araştırın.
- [ ] Dosya sahipliği ile dosya izinleri arasındaki ilişkiyi açıklayın.

> [!info] **Araştırılacak Konular**
> `ls -l`, `chmod`, `chown`, `chgrp`, kullanıcı, grup, diğerleri (`ugo`), `rwx`, sayısal izinler (`644`, `755` vb.), dosya sahipliği mantığı.

---

## ⚡ Görev 6: Program Çalıştırma ve Süreç Yönetimi
Linux'ta programların nasıl çalıştırıldığını ve süreçlerin (process) nasıl takip edildiğini öğrenin.

### Yapılacaklar
- [ ] Terminal üzerinden bir program çalıştırın.
- [ ] Bir programın sistemde nerede bulunduğunu öğrenin.
- [ ] Çalışan süreçleri listeleyin.
- [ ] Çalışan bir programın PID (Process ID) değerini bulun.
- [ ] Arka planda bir komut çalıştırın.
- [ ] Bir sürecin nasıl sonlandırıldığını araştırın.
- [ ] Bir komutun başarıyla tamamlanıp tamamlanmadığını kontrol edin.

> [!tip] **Ek Görev**
> Basit bir Bash betiği (`.sh`) hazırlayın. Betik terminale bir mesaj yazdırsın ve ardından çalıştırılabilir hale getirilerek (`chmod +x`) çalıştırılsın.

> [!info] **Araştırılacak Konular**
> `./program`, `PATH`, `which`, `command -v`, `ps`, `top`, `htop`, `pgrep`, `kill`, `jobs`, `bg`, `fg`, `&`, çıkış kodu (`$?`).

---

## 📦 Görev 7: Paket Yönetimi ve Root Kullanıcısı
Ubuntu üzerinde yazılım kurmayı, kaldırmayı ve yönetici yetkilerinin kullanımını öğrenin.

### Yapılacaklar
- [ ] Sistemde kurulu olan paketleri araştırın.
- [ ] Paket listelerini güncelleyin.
- [ ] Sisteme `tree` programını kurun.
- [ ] `tree` programını terminalden çalıştırın.
- [ ] Programın sistemde nerede bulunduğunu öğrenin.
- [ ] Kurduğunuz programı sistemden kaldırmayı araştırın.
- [ ] Normal kullanıcı ile `root` kullanıcısı arasındaki farkı açıklayın.

> [!warning] **Dikkat**
> Paket kurma ve kaldırma işlemlerinde `sudo` kullanmanız gerekebilir. İnternetten bulduğunuz komutları ne yaptıklarını anlamadan yönetici yetkisiyle çalıştırmayın.

> [!info] **Araştırılacak Konular**
> `apt update`, `apt install`, `apt remove`, `sudo`, `su`, root kullanıcısı, yönetici yetkileri, paket ve bağımlılık kavramları.

---

## 🖥️ Görev 8: Sistem Bilgileri ve Donanım
Kullandığınız Linux sistemini ve donanım bileşenlerini terminal üzerinden inceleyin.

### Yapılacaklar
- [ ] Linux dağıtımınızı ve sürümünü öğrenin.
- [ ] Çekirdek (Kernel) sürümünü öğrenin.
- [ ] İşlemci (CPU) ve RAM bilgilerini görüntüleyin.
- [ ] Disk kullanımını inceleyin.
- [ ] Ağ arayüzlerini listeleyin.
- [ ] IP adresinizi öğrenin.
- [ ] Çalışan sistemin ne kadar süredir açık olduğunu öğrenin.

> [!info] **Araştırılacak Konular**
> `uname`, `cat /etc/os-release`, `lscpu`, `free`, `df`, `du`, `ip`, `hostname`, `uptime`, `lspci`, `lsusb`.

---

## 🌐 Görev 9: Ağ, İndirme ve Log Dosyaları
İHA yazılımlarında ve uzak sistemlerle çalışırken ihtiyaç duyulacak temel ağ ve sistem inceleme becerilerini geliştirin.

### Yapılacaklar
- [ ] Ağ arayüzlerinizi ve IP adreslerinizi görüntüleyin.
- [ ] Bir hedefin ağ üzerinden erişilebilirliğini `ping` ile test edin.
- [ ] Bir alan adının (domain) IP adresini öğrenin.
- [ ] Terminal üzerinden bir dosya indirin.
- [ ] Bir web sunucusuna HTTP isteği gönderin ve yanıtını inceleyin.
- [ ] Sistem loglarının bulunduğu dizini keşfedin.
- [ ] Bir log dosyasının son satırlarını canlı/statik görüntüleyin.

> [!tip] **Ek Görev**
> Bir komutun çıktısını dosyaya kaydedin ve `grep` kullanarak bu dosya içerisindeki belirli bir hata veya kelimeyi arayın.

> [!info] **Araştırılacak Konular**
> `ping`, `ip addr`, `ip route`, `ip a`, `curl`, `wget`, `journalctl`, `/var/log`, DNS, HTTP, ağ arayüzü kavramları.

---
#linux #terminal #devops #notes #rehber