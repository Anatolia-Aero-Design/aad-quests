# 🤖 İHA'nın Sinir Sistemi: ROS2'ye Giriş

> [!abstract] **Amaç**
> İHA'da kamera, otonom kontrolcüsü, görüntü işleme gibi birimler birbirinden bağımsız modüller olarak çalışır. Bu modüllerin birbiriyle konuşmasını sağlayan sisteme ROS2 diyoruz. Bu quest'te ROS2'nin ne olduğunu anlayacak, ilk çalışma ortamını kuracak ve kendi yazdığın iki node'un birbirleriyle haberleştiğini göreceksin.

---

## 🔧 Görev 1: ROS2 Nedir ve Neden Kullanıyoruz?

İHA yazılımını tek bir dev Python dosyasına yazmayı düşün: kamera işleme, otonom, veri işleme... Her şey iç içe. Düzenlemesi ve geliştirmesi çok zor, bir kod çökünce bütün sistem çöküyor.

**ROS2 (Robot Operating System 2)** bu sorunu çözmek için var. Her modül bağımsız bir **node** olarak çalışır ve birbirleriyle **topic** adı verilen kanallar üzerinden mesaj gönderip alır. Kamera node'u bir nesne tespit ettiğinde bunu bir topic'e yazar; otonom node'u onu okur ve harekete geçer. Hiçbiri diğerinin iç yapısını bilmek zorunda değil.

> [!info] **Araştırılacak Konular**
> ROS2 DDS (Data Distribution Service) nedir? [Çıkmış soru, hakem yarışmada bana sordu :D (erdeniz)] 
> `rclpy` nedir (Python ROS2 istemcisi)?

---

## 🔧 Görev 2: Temel Kavramlar

Koda geçmeden önce terminolojiyi oturt. Bunlar ROS2'de her gün kullanacağın kelimeler.
### Yapılacaklar
- [ ] Aşağıdaki tabloyu oku ve her kavramı kendi cümlelerinle bir yere not et.

| Kavram | Ne anlama gelir |
|---|---|
| **Node** | Tek bir görevi yapan bağımsız süreç (program). Örn: `kamera_node`, `gps_node` |
| **Topic** | Node'ların mesaj yayınladığı/dinlediği isimli kanal. Örn: `/tespit_koordinatlari` |
| **Message** | Topic üzerinden gönderilen veri tipi. Örn: `std_msgs/String`, `geometry_msgs/Point` |
| **Publisher** | Bir topic'e mesaj gönderen taraf |
| **Subscriber** | Bir topic'i dinleyip mesajları alan taraf |
| **Package** | İlgili node'ları, launch dosyalarını ve bağımlılıkları bir arada tutan klasör |
| **Workspace** | Birden fazla package'ı derleyip yönettiğin ana çalışma dizini |

Kod tabanımızdan örnek topic ve subscriber:

```
[ image_processing ]                     [ otonom ]
  Publisher                           Subscriber
  topic: img_proc  --------->  topic: img_proc
  msg: savasan_general/ImgProc             msg: savasan_general/ImgProc
```

> [!info] **Araştırılacak Konular**
> `Service` ve `Topic` kavramları nedir?, `QoS (Quality of Service)` politikası neden önemli?, `launch file` ne işe yarar?

---

## 🔧 Görev 3: ROS2 Jazzy Kurulumu (Ubuntu 24.04)

### Yapılacaklar
- [ ] Sistemi güncelle:

```bash
sudo apt update && sudo apt upgrade -y
```

- [ ] ROS2 GPG anahtarını ekle:

```bash
sudo apt install -y software-properties-common curl
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key \
  -o /usr/share/keyrings/ros-archive-keyring.gpg
```

- [ ] ROS2 paket deposunu sisteme ekle:

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] \
  http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" \
  | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

- [ ] Depoyu güncelle ve ROS2 Jazzy'yi kur:

```bash
sudo apt update
sudo apt install -y ros-jazzy-desktop
```

- [ ] Geliştirme araçlarını da kur:

```bash
sudo apt install -y python3-colcon-common-extensions python3-rosdep ros-dev-tools
```

- [ ] ROS2 ortamını her terminalde otomatik aktif hale getir:

```bash
echo "source /opt/ros/jazzy/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

- [ ] Kurulumu doğrula — terminale bunu yaz ve bir `talker` başlat:

```bash
ros2 run demo_nodes_py talker
```

Başka bir terminalde dinleyiciyi başlat:

```bash
ros2 run demo_nodes_py listener
```

İki terminal arasında mesajlar aktığını görüyorsan kurulum başarılı. `Ctrl+C` ile durdur.

> [!warning] **source Komutu Unutulursa**
> `ros2: command not found` hatası alıyorsan büyük ihtimalle `source /opt/ros/jazzy/setup.bash` çalıştırılmamış demektir. `.bashrc`'ye eklediğinden emin ol veya terminali yeniden başlat.

> [!info] **Araştırılacak Konular**
> `colcon` nedir?, `rosdep` ne işe yarar?, `setup.bash` source edilince ne olur?

---

## 🔧 Görev 4: Workspace Oluşturma ve Derleme

ROS2'de her proje bir **workspace** içinde yaşar.

### Yapılacaklar
- [ ] Workspace dizinini oluştur:

```bash
mkdir -p ~/ros2_ws/src
cd ~/ros2_ws
```

- [ ] Şimdilik `src` boş olsa bile derle (her şeyin çalıştığını teyit eder):

```bash
colcon build
```

- [ ] Derleme sonrası oluşan `install` dizinini aktif hale getir:

```bash
source install/setup.bash
```

- [ ] Bu komutu da `.bashrc`'ye ekle ki her terminalde otomatik çalışsın:

```bash
echo "source ~/ros2_ws/install/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

Dizin yapısı şu şekilde görünmeli:

```
ros2_ws/
├── build/       ← colcon build sırasında oluşur
├── install/     ← derlenmiş çalıştırılabilir dosyalar
├── log/         ← build logları
└── src/         ← kendi package'larını buraya yazarsın
```

> [!info] **Araştırılacak Konular**
> `colcon build --symlink-install` ne işe yarar?, `COLCON_IGNORE` dosyası ne zaman kullanılır?, Workspace overlaying (üst üste workspace) mantığı.

---

## 🔧 Görev 5: İlk Package'ı Oluştur

Artık bir package yazıp içine node koyabiliriz.

### Yapılacaklar
- [ ] `src` dizinine geç ve Python package oluştur:

```bash
cd ~/ros2_ws/src
ros2 pkg create --build-type ament_python merhaba_dunya_pkg
```

- [ ] Oluşan dizin yapısına bak:

```bash
ls merhaba_dunya_pkg/
```

Şunu görmelisin:

```
merhaba_dunya_pkg/
├── merhaba_dunya_pkg/   ← Python modülü (node dosyaları buraya)
│   └── __init__.py
├── package.xml          ← package metaverisi ve bağımlılıklar
├── resource/
├── setup.cfg
└── setup.py             ← hangi script'lerin kurulacağı
```

> [!info] **Araştırılacak Konular**
> `package.xml` içindeki `<depend>` tagları ne anlama gelir?, `ament_python` ve `ament_cmake` farkı nedir?, `setup.py`'deki `entry_points` ne işe yarar?

---

## 🔧 Görev 6: Publisher Node Yaz

Her saniye bir mesaj yayınlayan bir node yazalım.

### Yapılacaklar
- [ ] `merhaba_dunya_pkg/` Python modül dizininde `yayinci.py` adında bir dosya oluştur:

```bash
nano ~/ros2_ws/src/merhaba_dunya_pkg/merhaba_dunya_pkg/yayinci.py
```

- [ ] Aşağıdaki kodu yaz:

```python
import rclpy
from rclpy.node import Node
from std_msgs.msg import String


class Yayinci(Node):
    """
    '/merhaba' topic'ine her saniye bir String mesajı yayınlayan node.
    """

    def __init__(self):
        # Node'un adını belirtiyoruz. Bu isim 'ros2 node list' ile görünür.
        super().__init__('yayinci_node')

        # Publisher oluşturuyoruz:
        #   - String mesaj tipi kullanacağız (std_msgs/String)
        #   - Topic adı: '/merhaba'
        #   - queue_size (QoS): 10 — bağlantı koparsa en fazla 10 mesajı hafızada tutar
        self.publisher_ = self.create_publisher(String, '/merhaba', 10)

        # Her 1.0 saniyede bir 'zamanlayici_callback' fonksiyonunu çağır
        self.timer = self.create_timer(1.0, self.zamanlayici_callback)

        # Kaçıncı mesaj gönderildiğini saymak için sayaç
        self.sayac = 0

        self.get_logger().info("Yayıncı node başladı, mesaj gönderiliyor...")

    def zamanlayici_callback(self):
        """Timer her tetiklendiğinde bu fonksiyon çalışır."""
        mesaj = String()
        mesaj.data = f'Merhaba İHA! Mesaj numarası: {self.sayac}'

        # Mesajı topic'e yayınla
        self.publisher_.publish(mesaj)

        self.get_logger().info(f'Yayınlandı: "{mesaj.data}"')
        self.sayac += 1


def main(args=None):
    # ROS2 Python istemcisini başlat
    rclpy.init(args=args)

    # Node'umuzu oluştur
    yayinci = Yayinci()

    # Node'u döngüde çalıştır (Ctrl+C ile durdurana kadar)
    rclpy.spin(yayinci)

    # Temiz çıkış
    yayinci.destroy_node()
    rclpy.shutdown()


if __name__ == '__main__':
    main()
```

- [ ] `setup.py` dosyasını aç ve `entry_points` bölümüne node'u ekle:

```python
entry_points={
    'console_scripts': [
        'yayinci = merhaba_dunya_pkg.yayinci:main',
        # dinleyici.py'yi yazdıktan sonra buraya da ekleyeceksin
    ],
},
```

> [!info] **Araştırılacak Konular**
> `rclpy.spin()` ne yapar?, `create_timer` yerine başka hangi yöntemlerle periyodik işlem yapılabilir?, `QoS` profilleri: `RELIABLE` vs `BEST_EFFORT`.

---

## 🔧 Görev 7: Subscriber Node Yaz

Şimdi yayıncının gönderdiği mesajları dinleyecek bir node yazalım.

### Yapılacaklar
- [ ] Aynı dizinde `dinleyici.py` dosyası oluştur:

```bash
nano ~/ros2_ws/src/merhaba_dunya_pkg/merhaba_dunya_pkg/dinleyici.py
```

- [ ] Aşağıdaki kodu yaz:

```python
import rclpy
from rclpy.node import Node
from std_msgs.msg import String


class Dinleyici(Node):
    """
    '/merhaba' topic'ini dinleyen ve gelen mesajları ekrana yazan node.
    """

    def __init__(self):
        super().__init__('dinleyici_node')

        # Subscriber oluşturuyoruz:
        #   - String mesaj tipi bekliyoruz
        #   - '/merhaba' topic'ini dinliyoruz
        #   - Mesaj geldiğinde 'mesaj_alindi_callback' çağrılacak
        self.subscription = self.create_subscription(
            String,
            '/merhaba',
            self.mesaj_alindi_callback,
            10  # queue_size
        )

        self.get_logger().info("Dinleyici node başladı, '/merhaba' topic'i bekleniyor...")

    def mesaj_alindi_callback(self, mesaj):
        """Topic'ten her mesaj geldiğinde bu fonksiyon otomatik çalışır."""
        self.get_logger().info(f'Alındı: "{mesaj.data}"')


def main(args=None):
    rclpy.init(args=args)

    dinleyici = Dinleyici()

    # Mesaj gelene kadar bekle, gelince callback'i çalıştır
    rclpy.spin(dinleyici)

    dinleyici.destroy_node()
    rclpy.shutdown()


if __name__ == '__main__':
    main()
```

- [ ] `setup.py` dosyasına dinleyiciyi de ekle:

```python
entry_points={
    'console_scripts': [
        'yayinci = merhaba_dunya_pkg.yayinci:main',
        'dinleyici = merhaba_dunya_pkg.dinleyici:main',
    ],
},
```

> [!info] **Araştırılacak Konular**
> `callback` (geri çağırım) fonksiyonu mantığı, Aynı topic'i birden fazla subscriber dinleyebilir mi?, Publisher ve Subscriber aynı node içinde olabilir mi?

---

## 🔧 Görev 8: Derle ve İkisini Birden Çalıştır

### Yapılacaklar
- [ ] Workspace'e dön ve derle:

```bash
cd ~/ros2_ws
colcon build --packages-select merhaba_dunya_pkg
```

- [ ] Yeni derlemeyi aktif et:

```bash
source install/setup.bash
```

- [ ] **Terminal 1'de** yayıncıyı başlat:

```bash
ros2 run merhaba_dunya_pkg yayinci
```

- [ ] **Terminal 2'de** dinleyiciyi başlat:

```bash
ros2 run merhaba_dunya_pkg dinleyici
```

Terminal 2'de yayıncının gönderdiği mesajların göründüğünü görmelisin:

```
[INFO] [dinleyici_node]: Alındı: "Merhaba İHA! Mesaj numarası: 0"
[INFO] [dinleyici_node]: Alındı: "Merhaba İHA! Mesaj numarası: 1"
[INFO] [dinleyici_node]: Alındı: "Merhaba İHA! Mesaj numarası: 2"
```

> [!important] **İki Node Birbirini Tanıdı!**
> `yayinci_node` ve `dinleyici_node` birbirini doğrudan tanımıyor. Sadece aynı topic adını (`/merhaba`) kullanıyorlar. Bu, ROS2'nin temel gücü: node'lar birbirinden bağımsız, topic ise köprü.

---

## 🔧 Görev 9: Debug Komutları ile Sistemi Keşfet

Node'lar çalışırken başka bir terminalde şu komutları dene.

### Yapılacaklar
- [ ] Çalışan tüm node'ları listele:

```bash
ros2 node list
```

Çıktı:
```
/yayinci_node
/dinleyici_node
```

- [ ] Aktif topic'leri listele:

```bash
ros2 topic list
```

- [ ] Bir topic üzerindeki mesajları canlı izle:

```bash
ros2 topic echo /merhaba
```

- [ ] Topic'in mesaj tipini ve yayın hızını öğren:

```bash
ros2 topic info /merhaba
ros2 topic hz /merhaba
```

- [ ] Bir node hakkında detaylı bilgi al (hangi topic'leri yayınlıyor/dinliyor):

```bash
ros2 node info /yayinci_node
```

- [ ] **Bonus:** Node'lar arasındaki bağlantı grafiğini görsel olarak aç:

```bash
rqt_graph
```

> [!tip] **rqt_graph Çok Kullanışlı**
> İHA yazılımı büyüdükçe onlarca node ve topic olacak. `rqt_graph` hangi node'un hangi topic'e bağlı olduğunu görsel olarak gösterir — hata ayıklamada çok işe yarar.

> [!info] **Araştırılacak Konular**
> `ros2 bag record` ile topic verileri nasıl kaydedilir ve oynatılır?, `ros2 param` ile node parametreleri nasıl yönetilir?, `ros2 interface show std_msgs/msg/String` ne gösterir?

---

#ros2 #jazzy #rclpy #node #topic #publisher #subscriber #python #iha #linux
