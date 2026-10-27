# CLAUDE.md — aad-quests Proje Rehberi

Bu dosya, **Claude AI** ve benzeri yapay zeka ajanların bu repoda etkin şekilde çalışabilmesi için hazırlanmıştır. Reponun amacını, yapısını, içerik standartlarını ve tasarım ilkelerini tanımlar.

---

## 📌 Proje Özeti

**aad-quests**, bir İHA (İnsansız Hava Aracı) yazılım takımının yeni üyelerini yetiştirmek için tasarlanmış, "quest" (görev/macera) formatında yapılandırılmış eğitim materyali reposudur.

| Özellik | Değer |
|---|---|
| **Amaç** | Yazılım takımı üyelerini Tier 1'den Tier 3'e yetkinleştirmek |
| **Hedef Kitle** | Yazılım geçmişi olmayan yeni başlayanlardan ileri düzey uzmanlara kadar |
| **Platform** | Obsidian (Markdown vault) |
| **Birincil Dil** | Türkçe (teknik terimler İngilizce kalabilir) |
| **Varsayılan Programlama Dili** | Python |
| **ROS Versiyonu** | ROS2 Jazzy |

---

## 🗂️ Dosya Yapısı

```
aad-quests/
├── CLAUDE.md                          ← Bu dosya
├── README.md                          ← GitHub'da görünen kısa tanıtım
├── LICENSE
├── Hayvanlar/                         ← Obsidian görsel varlıkları (dokunma)
└── Quests/                            ← Tüm eğitim içeriğinin ana klasörü
    ├── .obsidian/                     ← Obsidian yapılandırmaları (dokunma)
    ├── INDEX.md                       ← Tier'lara bağlantı indeksi
    ├── Yazılımcı/                     ← Tier 1
    │   ├── Yazılımcı.md               ← Tier giriş sayfası (quest listesi)
    │   ├── Linux.md
    │   ├── Github.md
    │   └── Python.md
    ├── AAD Yazılımcısı/               ← Tier 2
    │   ├── AAD Yazılımcısı.md         ← Tier giriş sayfası (quest listesi)
    │   ├── Görüntüyü İşlemeyi Anlamak.md    ✅ Tamamlanmış
    │   ├── Temel Otonom ve Yer İstasyonu Bilgisi.md  ✅ Tamamlanmış
    │   ├── ROS'u Bilmek.md            ✅ Tamamlanmış
    │   ├── Donanımları tanımak.md     ✅ Tamamlanmış
    │   ├── Sistemi Anlamak.md         ⚠️ İÇERİK YOK — DOKUNMA
    │   └── Veri İşlemeyi Anlamak.md  ⚠️ İÇERİK YOK — DOKUNMA
    └── Usta AAD Yazılımcısı/          ← Tier 3
        └── Usta AAD Yazılımcısı.md   (Henüz geliştirilmekte)
```

---

## 🏆 Tier Sistemi

Repo, üç kademeli bir ilerleme sistemi üzerine inşa edilmiştir. Her tier bir öncekinin tamamlanmasını gerektirir.

### Tier 1 — Yazılımcı (Herkes)
**Konu:** Genel yazılım geliştirme temelleri  
**Hedef:** Tüm takım üyeleri bu seviyeyi tamamlar.  
**Quests:** Linux, Git & GitHub, Python

### Tier 2 — AAD Yazılımcısı (Çoğu kişi)
**Konu:** İHA'ya özgü yazılım ve sistem bilgisi  
**Hedef:** Takımın büyük çoğunluğu bu seviyeye ulaşır.  
**Quests:** Görüntü İşleme (OpenCV), Otonom Uçuş & QGC, Veri İşleme, ROS2, Donanım Entegrasyonu, Sistem Mimarisi

### Tier 3 — Usta AAD Yazılımcısı (Uzmanlar)
**Konu:** İleri düzey sistem entegrasyonu, özgün geliştirme  
**Hedef:** Takıma liderlik edebilecek, derinlemesine uzmanlaşmış bireyler.  
**Quests:** Henüz aktif geliştirme aşamasında.

---

## ✍️ İçerik Yazma Kuralları / Quest Format Standardı

### Obsidian Callout Türleri

Callout'lar tutarlı ve amaçlarına uygun kullanılmalıdır:

| Callout | Ne Zaman Kullanılır |
|---|---|
| `> [!abstract]` | Quest'in en üstünde, **Amaç** bölümü olarak. Öğrenci bu bölümü okuyarak ne yapacağını anlamalı. |
| `> [!info]` | **Araştırılacak Konular** listesi için. Her görev bloğunun sonuna eklenir. Öğrenciyi aktif araştırmaya yönlendirir. |
| `> [!tip]` | İpuçları, kısa ama kritik bağlam bilgileri, doğru yönlendirmeler. |
| `> [!warning]` | Dikkat edilmesi gereken tehlikeli ya da kritik noktalar (ör: yanlış komut sisteme zarar verebilir). |
| `> [!note]` | Arka plan bilgisi ya da kavramsal açıklamalar. |

**Tebrikler veya motivasyon mesajları** için `> [!info]` kullanmak kabul edilebilir (örn: `> [!info] **Tebrikler!**`).

### Görev Numaralama Formatı

Her görev bloğu aşağıdaki başlık formatıyla başlar:

```markdown
## 🛠️ Görev 1: Kısa ve Açıklayıcı Başlık
```

- Başlık seviyesi: `##` (ikinci düzey başlık)
- Emoji: göreve uygun seçilmeli (🛠️ kurulum, 🎯 hedef, 🚀 ileri adım, 🗺️ planlama vb.)
- Format: `## <emoji> Görev <N>: <Başlık>`
- Numaralandırma: sıralı (1, 2, 3…)

Altında kısa bir açıklama paragrafı (1–3 cümle) bulunur, ardından `### Yapılacaklar` alt başlığı gelir.

### Checkbox Yapısı

Yapılacak her madde, Obsidian'da tıklanabilir checkbox formatında yazılır:

```markdown
- [ ] Yapmak gereken şey açık ve net biçimde ifade edilir.
- [ ] Gerekirse komut satırı örnekleri backtick içinde verilir: `pip install opencv-python`
- [ ] Sıralı adımlar için numaralı liste iç içe kullanılabilir.
```

### `Araştırılacak Konular` Standardı

Her görev bloğunun sonuna araştırmayı teşvik eden bir `[!info]` callout eklenir:

```markdown
> [!info] **Araştırılacak Konular**
> `anahtar_kelime_1`, `anahtar_kelime_2`, Kavram Adı, ilgili fonksiyon veya komut.
```

- Konular virgülle ayrılır.
- Teknik terimler (fonksiyon adları, komutlar) backtick içinde gösterilir.
- Soru formunda da yazılabilir: `> Groundspeed ile Airspeed'in farkı nedir?`
- Bu bölüm **cevapları vermez**, öğrencinin araştırmasını sağlar.

### Python Kodu Standartları

- **Tüm kod tam ve çalışır olmalıdır.** Eksik, placeholder içeren ya da çalışmayan kod snippet'i bırakma.
- **Her satır ya da mantıksal blok Türkçe yorumla açıklanmalıdır.**
- Değişken adları Türkçe veya mantıklı İngilizce olabilir (tutarlılık önemli).
- Kod, öğrenci terminale yapıştırınca çalışmalı.

```python
# ✅ DOĞRU: Yorumlanmış, tam, çalışır
kamera = cv2.VideoCapture(0)  # 0 = varsayılan kamera

# ❌ YANLIŞ: Yorumsuz, eksik, placeholder içeren
cap = cv2.VideoCapture(...)  # TODO: implement
```

### Türkçe Dil Standardı

- Tüm açıklama metinleri, görev tanımları ve yorumlar **Türkçe** yazılır.
- Yaygın kullanılan teknik terimler (commit, push, fork, node, topic, waypoint vb.) **İngilizce** bırakılır; zorunlu değilse çevrilmez.
- Karmaşık bir terimi ilk kez kullanırken kısa bir parantez açıklaması eklenebilir: `Kontür (kontur)`.
- Resmi ve ders kitabı tonu yerine samimi, konuşan bir dil tercih edilir.

---

## 🎮 Quest Tasarım İlkeleri

### "Quest" Havası Yaratma

Bu repo bir ders kitabı değil, bir **macera haritasıdır**. İçerik yazarken şu prensipleri gözetle:

- Görevler birbirinin üzerine inşa edilir; öğrenci her adımda bir şeyler çalıştırır, görür, hisseder.
- Görev başlıklarında aksiyon yönlendirici fiil ya da emoji kullan: `🛫 Görev 3: Uçuş Öncesi Kontroller ve Kalkış`
- Bir görevin başında neden yaptıklarını açıkla: öğrenci "bu ne işe yarayacak?" diye sormamalı.
- Quest'in sonunda bir **"Sonuç / Tebrik"** bölümü eklemek öğrenciyi motive eder.

### Yardım Etme ile Kendi Başına Yapma Dengesi

| Durum | Ne Yapılır |
|---|---|
| **Temel kurulum / boilerplate kod** | Doğrudan ver; öğrencinin zamanını kopyalamaya harcamasın. |
| **Anlaşılması gereken core mantık** | Kodu ver, ama her satırını yorumla. Öğrenci sadece çalıştırmaz, okur. |
| **Araştırılabilir kavramlar** | Kodu verme; `[!info] Araştırılacak Konular` ile yönlendir. |
| **Geliştirme önerileri** | Kodun sonuna "Bunu dene!" tarzı opsiyonel meydan okumalar eklenebilir. |

**Kural:** Öğrenci bir sonraki adıma geçebilmeli ama her adımda bir şeyi araştırıp anlamalı.

### Yeni Başlayanlara Hitap

- Jargon kullanmadan önce kısa tanım ver ya da araştırmaya yönlendir.
- Terminale yapıştırılmaya hazır komutlar ver; `<buraya yaz>` şeklinde placeholder bırakma.
- "Bunu neden yapıyoruz?" sorusunu `[!tip]` veya açıklama paragrafıyla cevapla.
- Hata mesajlarından korkmama konusunda cesaretlendir (örn: Linux quest'indeki "panik yapmayın" notu).

---

## ⚠️ İçerik Yazılmamış Dosyalar — DOKUNMA

Aşağıdaki dosyalar repo'da yer almakla birlikte **henüz içerik yazılmamıştır**. Bu dosyalar yapay zeka ajanlar tarafından doldurulmamalı, içerikleri değiştirilmemeli ve silinmemelidir:

| Dosya | Tier | Durum |
|---|---|---|
| `Quests/AAD Yazılımcısı/Sistemi Anlamak.md` | Tier 2 | ⚠️ Boş — içerik bekleniyor |
| `Quests/AAD Yazılımcısı/Veri İşlemeyi Anlamak.md` | Tier 2 | ⚠️ Boş — içerik bekleniyor |

Bu dosyalara yönelik bir görev alınırsa, değişikliği yapmadan önce kullanıcıya sor.

---

## 🔀 Tier Geçiş Koşulları

| Geçiş | Koşul |
|---|---|
| **Tier 1 → Tier 2** | Linux, Git & GitHub, Python quest'lerindeki tüm checkbox'lar tamamlanmış olmalı. |
| **Tier 2 → Tier 3** | Tier 2'deki tüm quest'ler tamamlanmış ve varsa teslim edilmesi gereken çalışmalar (kod, PR vb.) yapılmış olmalı. |

> **Not:** Tier geçiş kriterleri takım liderliği tarafından onaylanır. Checkbox'ların tamamlanmış olması tek başına yeterli olmayabilir; anlayış düzeyi de değerlendirilebilir.

---

## ✅ Örnek İyi Dosyalar (Referans Al)

Yeni içerik yazarken aşağıdaki dosyaları **stil, ton ve format için referans** olarak kullan:

### 1. `Quests/AAD Yazılımcısı/Görüntüyü İşlemeyi Anlamak.md`
- **Neden iyi:** Görevler kümülatif olarak birbirinin üzerine inşa edilmiş. Her görev bir öncekinin koduna ekleme yapıyor. Tam ve yorumlanmış kod blokları, her görev sonunda `[!info] Araştırılacak Konular`, quest'in sonunda birleştirilmiş "master kod" ve tebrik callout'u var.

### 2. `Quests/AAD Yazılımcısı/Temel Otonom ve Yer İstasyonu Bilgisi.md`
- **Neden iyi:** Kodu olmayan (simülatör & arayüz tabanlı) bir quest'in nasıl yazılacağını gösteriyor. Checkbox'lar somut ve doğrulanabilir. `[!warning]` ile kritik güvenlik notu eklemiş. Teknik terimlerin soru formatında araştırılması (`Airspeed vs Groundspeed nedir?`) iyi bir örnek.

---

## 🛠️ Yeni Quest Ekleme Akışı

1. Quest dosyasını ilgili Tier klasörüne oluştur (`Quests/<Tier Adı>/<Quest Adı>.md`).
2. Tier'ın giriş sayfasına (`Yazılımcı.md`, `AAD Yazılımcısı.md` vb.) Obsidian iç linki ekle: `[[Quest Adı]]`.
3. Dosya başlığını `# <Emoji> <Quest Başlığı>` formatında yaz.
4. İlk iki callout: `[!abstract]` (Amaç) ve varsa `[!warning]` (Önemli kurallar).
5. `---` ile ayır, `## <Emoji> Görev N: Başlık` ile her görevi yaz.
6. Her görev altında: kısa açıklama → `### Yapılacaklar` → checkbox'lar → `[!info] Araştırılacak Konular`.
7. Son bölüm: sonuç veya tebrik.
8. Dosyanın en altına ilgili etiketler: `#python #ros2 #iha #konu-adı`
