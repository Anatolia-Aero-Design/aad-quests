# ✈️ ArduPilot & QGC: Sabit Kanat Temel Görev Eğitimi

> [!abstract] **Amaç**
> ArduPilot (ArduPlane) çalıştıran bir sabit kanat (Fixed-Wing) İHA'yı simülatör (SITL) ortamında başlatmak, QGroundControl (QGC) arayüzüne bağlamak, otonom bir kalkış-rota-iniş görevi planlamak ve görevi uçurarak telemetri takibi yapmak.

> [!warning] **Önemli Hatırlatma**
> Sabit kanatlı uçaklar, döner kanatlı (multirotor) dronlar gibi dikey kalkıp havada asılı kalamazlar. Uçabilmeleri için sürekli bir ileri hava hızına (Airspeed) ve kalkış/iniş için uygun pist veya yaklaşma açılarına ihtiyaç duyarlar.

---

## 🛠️ Görev 1: Simülasyonu Başlatma ve QGC Bağlantısı
Gerçek bir donanıma zarar vermeden önce adımları sanal bir uçak üzerinde test edeceğiz.

### Yapılacaklar
- [ ] Bilgisayarınızda QGroundControl (QGC) yazılımını başlatın.
- [ ] Terminali açın ve ArduPilot SITL üzerinden sabit kanat uçağını başlatın: `sim_vehicle.py -v ArduPlane --console --map`
- [ ] QGC'nin varsayılan UDP portu (14550) üzerinden uçağa otomatik bağlandığını doğrulayın (bağlantı kurulduğunda uçağın sesli bildirimi duyulur).
- [ ] Sol üstteki bağlantı çubuğundan GPS kilitlenmesini (3D Fix) ve batarya durumunu kontrol edin.
- [ ] Uçağın harita üzerinde doğru koordinatta ve DISARMED (motor kilitli) durumda olduğunu teyit edin.

> [!info] **Araştırılacak Konular**
> SITL mantığı, MAVLink protokolü, UDP 14550 portu, Disarmed vs. Armed durumu.

---

## 🗺️ Görev 2: Planlama Ekranında Otonom Görev Çizme
Uçağa kalkış yapacağı, havada dolaşacağı ve iniş yapacağı koordinatları içeren bir rota yükleyin.

### Yapılacaklar
- [ ] QGC sol üst menüsünden Plan (Planlama / Harita simgesi) görünümüne geçin.
- [ ] Uçağın bulunduğu noktaya yakın bir konumu Home (Kalkış Noktası) olarak belirleyin.
- [ ] Görev adımlarına sırasıyla şunları ekleyin:
  1. Takeoff (Kalkış): Uçağın pist doğrultusunda tırmanması için kalkış açısı (pitch) ve hedef irtifa (örn: 50m) belirleyin.
  2. Waypoint (Dönüş Noktaları): Uçağın havada bir üçgen veya kare rota çizmesi için en az 3 adet ara nokta ekleyin (İrtifayı 50m olarak koruyun).
  3. Loiter / Orbit (Bekleme - Opsiyonel): Belirli bir nokta etrafında 1 tur dönme komutu verin.
  4. Land (İniş): Rüzgara karşı olacak şekilde piste yaklaşma ve iniş noktasını yerleştirin.
- [ ] Sağ paneldeki "Upload" (Uçağa Yükle) butonuna basarak oluşturduğunuz görevi otopilota gönderin.

> [!tip] **Sabit Kanat İpucu**
> Waypoint dönüş açılarının çok keskin olmamasına dikkat edin. Sabit kanatların bir minimum dönüş yarıçapı vardır; çok dar açılarda uçak rotadan sapabilir.

---

## 🛫 Görev 3: Uçuş Öncesi Kontroller ve Kalkış
Planı tamamlanan uçağı havaya kaldırın.

### Yapılacaklar
- [ ] QGC menüsünden Fly (Uçuş) görünümüne geri dönün.
- [ ] QGC arayüzünden veya SITL konsolundan motorları devreye alın (Arm edin)
- [ ] Uçuş modunu TAKEOFF veya AUTO moduna alın.
- [ ] Uçağın motorunun devirlendiğini, simülasyon haritasında hızlanarak piste doğru koşturduğunu ve 50 metreye tırmandığını gözlemleyin.

> [!info] **Araştırılacak Konular**
> Sabit kanat uçuş modları: MANUAL, FBWA (Fly By Wire A), AUTO, RTL (Return to Launch).

---

## 🛰️ Görev 4: Uçuşu İzleme ve Acil Durum Müdahalesi
Uçak havadayken telemetri verilerini okuyun ve otopilot davranışını test edin.

### Yapılacaklar
- [ ] Uçağın harita üzerinde çizdiğiniz Waypoint noktalarını sırayla geçtiğini izleyin.
- [ ] Telemetri panelinden şu değerleri gözlemleyin ve ne olduklarını araştırın:
  - Groundspeed (Yer Hızı) vs. Airspeed (Hava Hızı)
  - Altitude (İrtifa)
  - Pitch / Roll açıları
- [ ] Uçak 2. veya 3. noktadayken acil durum senaryosu simüle edin: Uçuş modunu RTL (Return To Launch) moduna çekin.
- [ ] Uçağın mevcut rotayı bırakıp kalkış yaptığı noktanın üzerine dönerek çember çizmeye (Loiter) başladığını doğrulayın.

> [!info] **Araştırılacak Konular**
> Grodundspeed ile Airspeed in farkı nedir? 
> Pitch Roll Yaw nedir?

---

## 🛬 Görev 5: İniş ve Uçuşu Bitirme
Uçağı güvenli bir şekilde yere indirin ve motorları kilitleyin.

### Yapılacaklar
- [ ] Modu tekrar AUTO moduna alarak kalan iniş (Land) komutunu tamamlamasını sağlayın (veya doğrudan QGC'den Land komutu verin).
- [ ] Uçağın alçalma açısını koruyarak yere teker koymasını gözlemleyin.
- [ ] Yere indikten sonra motorların otomatik olarak kilitlendiğini (Disarmed) doğrulayın.
- [ ] QGC üzerinden uçağın bağlantısını sonlandırın.

---
#ardupilot #qgroundcontrol #fixed-wing #iha #sitl #otopilot #mission-planner