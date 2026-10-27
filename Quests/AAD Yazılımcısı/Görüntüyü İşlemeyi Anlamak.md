# 📷 OpenCV ile Görüntü İşleme: Canlı Nesne Tespiti

> [!abstract] **Amaç**
> Bilgisayarınızın kamerasını kullanarak etraftaki "kırmızı" nesneleri canlı olarak bulan, etrafına bir kare çizen ve ekranda etiketleyen bir program geliştirmek. Kodların ne işe yaradığını mantığıyla kavrayarak, boş bir dosyadan çalışan bir uygulamaya adım adım ilerleyeceğiz.

> [!tip] **Video İşlemenin Temeli**
> Video dediğimiz veri, aslında arka arkaya çok hızlı oynatılan fotoğraflardan (karelerden) ibarettir. Kameradan saniyede ortalama 30 fotoğraf alırız ve her bir fotoğrafı tek tek inceleriz. Bu yüzden kodumuzun kalbinde sürekli dönen bir `while` (döngü) olacak.

---

## 🛠️ Görev 1: Hazırlık ve Kamerayı Açma
Önce Python'a görüntü işleme yeteneği kazandıran OpenCV kütüphanesini kurmalı ve kameradan ilk görüntümüzü almalıyız.

### Yapılacaklar
- [ ] Terminalinizi açın ve şu komutu çalıştırarak gerekli araçları indirin: `pip install opencv-python numpy`
- [ ] Bilgisayarınızda `kirmizi_bul.py` adında boş bir dosya oluşturun.
- [ ] Aşağıdaki kodu yazın. Bu kod kamerayı açar, görüntüleri okur ve ekrana yansıtır.

```python
import cv2  
import numpy as np  

# Kameraya bağlanıyoruz. "0" bilgisayarın varsayılan kamerasını temsil eder.
kamera = cv2.VideoCapture(0)

# Video sürekli akan karelerden oluştuğu için sonsuz bir döngü başlatıyoruz.
while True:
    # Kameradan o anki fotoğrafı (kareyi) çekiyoruz.
    basarili_mi, kare = kamera.read() 
    
    # Eğer kameradan görüntü alamazsak döngüyü kırıp çıkıyoruz.
    if not basarili_mi:
        break
        
    # Aldığımız fotoğrafı ekranda bir pencerede gösteriyoruz.
    cv2.imshow("Kamera", kare)
    
    # Klavyeyi dinlemek için 1 milisaniye bekliyoruz.
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

kamera.release()
cv2.destroyAllWindows()
```
- [ ] Kodu çalıştırın. Kameranızın açıldığını ve klavyeden `q` tuşuna bastığınızda kapandığını test edin.

> [!info] **Araştırılacak Konular**
> `cv2.VideoCapture()`, `cv2.imshow()`, `cv2.waitKey()`, Python'da `while True` mantığı, OpenCV BGR formatı.

---

## 🎨 Görev 2: Renk Uzayını Değiştirmek (HSV Mantığı)
Kameralar renkleri normalde RGB (Kırmızı, Yeşil, Mavi) olarak algılar. Ancak ortamdaki ışık değiştiğinde bu üç değer de dalgalanır. Bunun yerine görüntüleri **HSV** (Renk, Doygunluk, Parlaklık) formatına çevireceğiz. Böylece ışık azalıp artsa bile "Renk" (Hue) değeri sabit kalacaktır.

### Yapılacaklar
- [ ] Yukarıdaki `while` döngüsünün içine (görüntüyü aldıktan hemen sonra) şu kodu ekleyin:

```python
    # Kameradan gelen normal resmi (BGR formatı), HSV formatına dönüştürüyoruz.
    hsv_kare = cv2.cvtColor(kare, cv2.COLOR_BGR2HSV)
```

> [!info] **Araştırılacak Konular**
> HSV (Hue, Saturation, Value) renk uzayı nedir?, RGB vs HSV farkı, Görüntü işlemede ışık (illumination) problemleri.

---

## 🎭 Görev 3: Kırmızı Rengi Filtreleme (Maske Oluşturma)
Şimdi görüntüdeki sadece kırmızı olan pikselleri BEYAZ, geri kalan her şeyi SİYAH yapacak bir "Maske" oluşturacağız.

### Yapılacaklar
- [ ] Kırmızı renk, HSV renk silindirinin hem en başında (0-10) hem de en sonunda (170-180) yer alır. Bu yüzden iki farklı aralık tanımlayıp bunları birleştireceğiz. Döngünün içine ekleyin:

```python
    # 1. Kırmızının ilk tonları için alt ve üst sınırlar
    alt_kirmizi1 = np.array([0, 100, 100])
    ust_kirmizi1 = np.array([10, 255, 255])
    maske1 = cv2.inRange(hsv_kare, alt_kirmizi1, ust_kirmizi1)

    # 2. Kırmızının diğer tonları için alt ve üst sınırlar
    alt_kirmizi2 = np.array([170, 100, 100])
    ust_kirmizi2 = np.array([180, 255, 255])
    maske2 = cv2.inRange(hsv_kare, alt_kirmizi2, ust_kirmizi2)

    # İki maskeyi topluyoruz. 
    maske = maske1 + maske2
```

> [!info] **Araştırılacak Konular**
> Maskeleme (Thresholding) mantığı, `cv2.inRange()`, NumPy dizileri (`np.array`), OpenCV Hue (H) değer aralıkları.

---

## 🧹 Görev 4: Gürültüleri Temizleme
Ekranda kırmızı olmayan ufak tefek ışık yansımaları da maskede beyaz noktalar olarak görünebilir. Hedefi doğru tespit edebilmek için bu "gürültüleri" temizlememiz gerekir.

### Yapılacaklar
- [ ] Maske kodundan hemen sonra, ufak pürüzleri silen morfolojik işlemi ekleyin:

```python
    # 5x5 piksel boyutunda bir çekirdek (kernel) oluşturuyoruz.
    firca = np.ones((5, 5), np.uint8)
    
    # MORPH_OPEN işlemi, maske üzerindeki ufak tefek beyaz noktaları silip temizler.
    maske = cv2.morphologyEx(maske, cv2.MORPH_OPEN, firca)
```

> [!info] **Araştırılacak Konular**
> Morfolojik işlemler (Morphological Operations), Erosion (Aşındırma) ve Dilation (Yayma), Kernel (Filtre matrisi) kavramı.

---

## 🎯 Görev 5: Şekilleri Bulma ve Kare Çizme
Elimizde temiz bir siyah/beyaz maske var. Maske üzerindeki beyaz alanların sınır çizgilerini (konturlarını) bulup, bu sınırların etrafına bir dikdörtgen çizeceğiz.

### Yapılacaklar
- [ ] Döngünün içine şu kodları ekleyerek nesne tespitini tamamlayın:

```python
    # Beyaz alanların sınırlarını (konturlarını) buluyoruz.
    konturlar, _ = cv2.findContours(maske, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)

    for kontur in konturlar:
        # Şeklin kapladığı alanı hesaplıyoruz.
        alan = cv2.contourArea(kontur)
        
        # Eğer şekil 500 pikselden büyükse (ufak yansımaları dışlamak için):
        if alan > 500:
            # Şekli içine alacak en uygun dikdörtgenin koordinatlarını alıyoruz.
            x, y, g, yuks = cv2.boundingRect(kontur)
            
            # Orijinal renkli görüntünün üzerine dikdörtgeni çiziyoruz.
            cv2.rectangle(kare, (x, y), (x + g, y + yuks), (0, 0, 255), 2)
            
            # Çizdiğimiz dikdörtgenin üzerine etiket yazdırıyoruz.
            cv2.putText(kare, "Kirmizi Cisim", (x, y - 10), cv2.FONT_HERSHEY_SIMPLEX, 0.7, (0, 0, 255), 2)
```

> [!info] **Araştırılacak Konular**
> Contours (Kontur bulma) nedir?, `cv2.findContours()`, Bounding Box (`cv2.boundingRect`), `cv2.rectangle`, `cv2.putText`.

---

## 🚀 Sonuç: Tüm Kodun Birleştirilmiş Hali
İşte baştan sona tüm aşamaları içeren, doğrudan kopyalayıp çalıştırabileceğiniz nesne tespiti kodumuz:

```python
import cv2
import numpy as np

# Kamerayı başlat
kamera = cv2.VideoCapture(0)

while True:
    basarili_mi, kare = kamera.read()
    if not basarili_mi:
        break

    # 1. Renklerin ışık değişiminden etkilenmemesi için HSV formatına çevir
    hsv_kare = cv2.cvtColor(kare, cv2.COLOR_BGR2HSV)

    # 2. Kırmızı rengin HSV sınırlarını belirle ve filtrele (Maskele)
    alt_kirmizi1 = np.array([0, 120, 70])
    ust_kirmizi1 = np.array([10, 255, 255])
    maske1 = cv2.inRange(hsv_kare, alt_kirmizi1, ust_kirmizi1)

    alt_kirmizi2 = np.array([170, 120, 70])
    ust_kirmizi2 = np.array([180, 255, 255])
    maske2 = cv2.inRange(hsv_kare, alt_kirmizi2, ust_kirmizi2)

    maske = maske1 + maske2

    # 3. Ufak gürültüleri (tozları/yansımaları) temizle
    firca = np.ones((5, 5), np.uint8)
    maske = cv2.morphologyEx(maske, cv2.MORPH_OPEN, firca)

    # 4. Beyaz bölgelerin sınırlarını (konturlarını) bul
    konturlar, _ = cv2.findContours(maske, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)

    for kontur in konturlar:
        alan = cv2.contourArea(kontur)
        
        # Tespit edilen kırmızılık yeterince büyükse işlemi yap
        if alan > 500: 
            x, y, g, yuks = cv2.boundingRect(kontur)
            
            # Orijinal görüntünün üzerine dikdörtgen çiz ve etiketle
            cv2.rectangle(kare, (x, y), (x + g, y + yuks), (0, 0, 255), 2)
            cv2.putText(kare, "Kirmizi Cisim", (x, y - 10), cv2.FONT_HERSHEY_SIMPLEX, 0.7, (0, 0, 255), 2)

    # 5. Sonuçları ekranda göster
    cv2.imshow("Orijinal Kamera", kare)
    cv2.imshow("Maske (Siyah/Beyaz Filtre)", maske)

    # Klavyeden 'q' tuşuna basılırsa döngüden çık
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

# İşlem bitince donanımları serbest bırak
kamera.release()
cv2.destroyAllWindows()
```

> [!info] **Tebrikler!**
> Temel bir yapay görme uygulamasını başarıyla tamamladınız. Otonom araçlar, endüstriyel robotlar ve otopilot sistemleri çevrelerini algılamak ve engellerden kaçınmak için temelde tam olarak bu mantığı (renkleri filtreleme, sınırları bulma, koordinat çıkarma) kullanırlar.

---
#python #opencv #computervision #görüntü-işleme