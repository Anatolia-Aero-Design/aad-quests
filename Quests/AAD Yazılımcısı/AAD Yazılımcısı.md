# 🚁 Tier 2 — AAD Yazılımcısı

> [!abstract] Bu Tier Hakkında
> Artık temellerin var. Şimdi gerçek işe giriyoruz. Bu tier seni sıradan bir yazılımcıdan **insansız hava aracı yazılım geliştiricisine** dönüştürür. Donanım, algılama, iletişim, otonom karar verme — hepsinin içinden geçeceksin.

---

## Neden Önemli?

Bir İHA sadece uçan bir nesne değil; sensörler, işlemciler, yazılım katmanları ve iletişim protokollerinden oluşan karmaşık bir sistem. Bu tier'ı tamamlayan biri sistemi hem parça parça hem de bütün olarak anlıyor. Ekipte asıl katkıyı bu seviyede yapmaya başlıyorsun.

> [!warning] Ön Koşul
> Bu tier'a başlamadan önce [[Yazılımcı]] tier'ını tamamlamış olmalısın. Tier 1 olmadan buradaki görevler çok daha sancılı olur.

---

## 📋 Görevler

### 🔌 [[Donanımları tanımak]]
İHA'nın fiziksel katmanı: Pixhawk uçuş kontrolcüsü, Jetson bilgisayar, kameralar, sensörler ve bunların birbirine bağlanma mantığı. Yazılımın altındaki donanımı tanımadan sağlıklı sistem geliştirmek güçtür. **Buradan başlamanı öneririz.**

### 👁️ [[Görüntüyü İşlemeyi Anlamak]]
Kamera görüntüsünü ham pikselden anlamlı bilgiye dönüştürme. OpenCV temelleri, görüntü pipeline'ı, nesne tespiti ve takibi. İHA gözleriyle ne gördüğünü anlamlandırmayı öğreneceksin.

### 📊 [[Veri İşlemeyi Anlamak]]
*Yapım Aşamasında 🚧*
Sensörlerden gelen ham veriyi temizleme, filtreleme ve anlamlandırma. IMU, GPS ve diğer sensörlerin çıktılarıyla çalışmayı öğreneceksin.

### 🤖 [[ROS'u Bilmek]]
Robot Operating System — takımın iletişim omurgası. Node'lar, topic'ler, servisler, action'lar. ROS2 olmadan sistemin parçaları birbirleriyle konuşamaz. Bu görevi tamamladığında ekosistemi anlayacak, kendi node'larını yazabileceksin.

### 🏗️ [[Sistemi Anlamak]]
*Yapım Aşamasında 🚧*
Tüm parçaların bir araya geldiği büyük tablo. Donanım, yazılım, iletişim katmanları ve bunların entegrasyonu. Sistemin tamamını uçtan uca görmek için bu görev.

### 🛰️ [[Temel Otonom ve Yer İstasyonu Bilgisi]]
İHA kendi başına nasıl karar verir? Görev planlaması, waypoint navigasyon, yer kontrol istasyonu (GCS) kullanımı ve otonom uçuş mantığı. Pilotun yerde olduğu ama İHA'nın havada kendi aklıyla hareket ettiği dünyaya giriş.

---

## 🏁 Tier'ı Tamamlamak Ne Anlama Geliyor?

Bu altı görevi bitirdiğinde:

- Sistemin donanımını tanıyor ve bağlantılarını anlıyorsun
- Görüntü işleme pipeline'ına katkı sağlayabiliyorsun
- ROS2 üzerinde node yazıp sisteme entegre edebiliyorsun
- Otonom uçuş mantığını ve yer istasyonunu kullanabiliyorsun
- Ekipte gerçek anlamda görev üstlenmeye hazırsın

> [!tip] Sıradaki Adım
> Tier 2'yi tamamlayanlar [[Usta AAD Yazılımcısı]] yoluna adım atabilir. Orada uzmanlık alanın belirleniyor ve derinleşiyorsun.

> [!info] Görev Sırası
> Bu tier içinde katı bir sıra yoktur; ancak **Donanımları tanımak** → **ROS'u Bilmek** → diğerleri şeklinde ilerlemenizi öneririz. Donanımı bilmek her şeyi daha somut kılar.
