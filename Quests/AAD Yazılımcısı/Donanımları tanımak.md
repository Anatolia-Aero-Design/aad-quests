# 🖥️ Donanımları Tanımak

> [!abstract] **Amaç**
> İHA yazılımının üzerinde koştuğu bilgisayarları, bunların ağda nasıl haberleştiğini ve bu cihazlara terminal üzerinden nasıl bağlanıldığını öğrenmek.

> [!important] **Donanım gerekmez**
> Bu quest teorik ve terminal tabanlıdır. Şimdilik kendi bilgisayarın yeterli.

---

## 🔧 Görev 1: Raspberry Pi ve Nvidia Jetson Nedir?

İHA yazılımları normal bir masaüstü bilgisayarda değil, küçük gömülü bilgisayarlarda çalışır. Bunların en yaygın ikisi Raspberry Pi ve Nvidia Jetson'dır.

### Yapılacaklar
- [ ] Aşağıdaki tabloyu okuyarak iki cihaz arasındaki farkı kavra.
- [ ] Araştır: Bu iki cihaz İHA projelerinde genellikle ne amaçla kullanılıyor?

| Özellik        | Raspberry Pi                                        | Nvidia Jetson                                     |
| -------------- | --------------------------------------------------- | ------------------------------------------------- |
| Ana güçlü yönü | Genel amaçlı kontrol, düşük güç tüketimi            | GPU sayesinde yapay zeka / görüntü işleme         |
| Tipik görev    | Basit işler. Sadece görüntü veya telemetri aktarma. | Nesne tespiti, derin öğrenme modelleri çalıştırma |
| Neden İHA'da?  | Hafif, ucuz                                         | Yapay zeka gerektiren görevler                    |

> [!info] **Araştırılacak Konular**
> `ARM işlemci` nedir?
> `GPU` neden yapay zeka için daha hızlı?

---

## 🔧 Görev 2: IP Adresi ve Port Nedir?

Bu cihazlara bağlanabilmek için ağın nasıl çalıştığını anlamak gerekir.

### Yapılacaklar
- [ ] Aşağıdaki açıklamayı okuyarak IP ve port kavramlarını somutlaştır.

**Benzetme:**
- **IP adresi** → Bir binanın sokak adresi. Ağdaki her cihazın kendine özgü bir adresi vardır. Örnek: `192.168.1.42`
- **Port numarası** → Binadaki daire numarası. Aynı IP'de çalışan farklı uygulamalar farklı portları kullanır.

| Port | Kullanım |
|---|---|
| `22` | SSH — uzak terminale bağlanmak |
| `80` | HTTP — web sayfaları |
| `443` | HTTPS — şifreli web |
| `14550` | MAVLink / QGroundControl — İHA haberleşmesi |
| `5760` | ArduPilot SITL çıkışı |

> [!info] **Araştırılacak Konular**
> `IPv4` vs `IPv6`, `localhost` ve `127.0.0.1` ne demek?, `subnet mask` nedir?, `192.168.x.x` neden özel (private) IP sayılır?

---

## 🔧 Görev 3: Basit Terminal Komutları

Kendi bilgisayarında dene.

### Yapılacaklar
- [ ] Ağ arayüzlerini ve IP adresini görüntüle:

```bash
ip addr
```

Çıktıda `eth0` (ethernet), `wlan0` (WiFi), `lo` (loopback) gibi arayüzler görürsün. `inet` ile başlayan satır IP adresini verir.

- [ ] Kısa özet için:

```bash
hostname -I
```

- [ ] Bilgisayarının ağ adını öğren:

```bash
hostname
```

- [ ] Kendine ping at — ağ bağlantısı olmadan da çalışır:

```bash
ping -c 4 127.0.0.1
```

`127.0.0.1` her zaman "bu bilgisayar" anlamına gelir.

> [!info] **Araştırılacak Konular**
> `ping` nasıl çalışır? (ICMP protokolü), `TTL` değeri ne anlama gelir?, `ip route` ile ağ geçidi (gateway) nasıl bulunur?

---

## 🔧 Görev 4: WiFi Kartı Nedir?

### Yapılacaklar
- [ ] Aşağıdaki tabloyu oku, 2.4 GHz ile 5 GHz arasındaki farkı kavra.
- [ ] Araştır: "dual-band" WiFi kartı ne demektir?
- [ ] Araştır: Kalabalık RF ortamlarında (yarışma alanı gibi) hangi frekans tercih edilmeli ve neden?

| Özellik                | 2.4 GHz                             | 5 GHz                         |
| ---------------------- | ----------------------------------- | ----------------------------- |
| Menzil                 | Daha uzun                           | Daha kısa                     |
| Hız                    | Düşük                               | Yüksek                        |
| Girişim (interference) | Çok fazla (komşu ağlar, mikrodalga) | Az                            |
| İHA'da tercih          | ❌ Gürültülü                         | ✅ Tercih edilen — temiz kanal |

> [!important] **Neden önemli?**
> Yarışma alanında onlarca WiFi ağı olabilir. 2.4 GHz'de bağlantı kesilir ya da gecikmeli hale gelir. 5 GHz daha az kalabalık ve daha az girişim demektir.

> [!info] **Araştırılacak Konular**
> `SSID` ve `BSSID` farkı nedir?, `monitor mode` ve `managed mode` ne demek?, WIFI kartı seçerken nelere bakılır?

---

#donanım #raspberry-pi #jetson #ssh #ağ #ip #port #wifi #terminal #linux
