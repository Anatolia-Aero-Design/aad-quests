# 🐙 Git & GitHub Başlangıç Eğitimi

> [!abstract] **Amaç**
> Git ve GitHub'ın ne olduğunu anlamak, temel kavramları öğrenmek ve ortak bir projeye (bu Obsidian vault'una) kendi bilgisayarınızdan ilk katkınızı (Pull Request) yapmak.

> [!warning] **Kurallar**
> - Acele etmeyin; komutları ezberlemek yerine "Şu an ne yapıyorum?" mantığını kavramaya çalışın.
> - Hata alırsanız panik yapmayın, terminaldeki hata mesajları genellikle çözümün ne olduğunu söyler.

---

## 🧠 Görev 1: Temel Kavramlar ve Hesap Oluşturma
Her şeyden önce kullandığımız araçları tanıyalım ve platforma katılalım.

### Yapılacaklar
- [ ] **Git nedir?** araştırın. (Kısa cevap: Dosyalarınızın zaman içindeki değişimini takip eden bir versiyon kontrol sistemidir).
- [ ] **GitHub nedir?** araştırın. (Kısa cevap: Git kullanarak yönetilen projelerin internet üzerinde tutulduğu, paylaşıldığı ve birlikte çalışıldığı platformdur).
- [ ] **Repository (Repo) nedir?** araştırın. (Kısa cevap: Projenizin tüm dosyalarını ve geçmişini tutan ana klasördür).
- [ ] [github.com](https://github.com/) adresine gidin ve kendinize ücretsiz bir hesap oluşturun.

---

## 🛠️ Görev 2: Git Kurulumu ve Kendini Tanıtma
Bilgisayarınızın Git'i kullanabilmesi için ufak bir hazırlık yapın.

### Yapılacaklar
- [ ] Bilgisayarınıza Git kurun (İşletim sisteminize göre internetten indirin).
- [ ] Terminali (veya Git Bash) açıp `git --version` yazarak kurulduğundan emin olun.
- [ ] Git'e adınızı tanıtmak için şu komutu çalıştırın: `git config --global user.name "Github isminiz"`
- [ ] Git'e e-postanızı tanıtmak için şu komutu çalıştırın: `git config --global user.email "github-epostaniz@mail.com"`

> [!tip] **Neden yapıyoruz?**
> Yaptığınız her kayıtta (commit) adınızın ve e-postanızın görünmesi zorunludur. Böylece projede kimin ne yaptığını herkes görebilir.

---

## 📥 Görev 3: Fork ve Klonlama (Repoyu İndirme)
Başkasına ait bir projede çalışabilmek için önce kendi kopyanızı almalı, sonra bilgisayarınıza indirmelisiniz.

### Yapılacaklar
- [ ] GitHub'da bu eğitimin bulunduğu ana depoya (repoya) gidin.
- [ ] Sağ üstteki **"Fork"** butonuna basın. (Bu işlem, ana projenin bir kopyasını *sizin* GitHub hesabınıza kopyalar).
- [ ] Şimdi *kendi hesabınızdaki* kopyaya gidin. Yeşil **"Code"** butonuna basıp web adresini (URL) kopyalayın.
- [ ] Terminali açın ve projeyi indirmek istediğiniz klasöre gidip şunu yazın: `git clone <kopyaladıgınız-url>`
- [ ] İndirme bitince terminalde klasörün içine girin: `cd <klasor-adi>`
- [ ] **Obsidian'ı açın**, "Open folder as vault" (Klasörü vault olarak aç) diyerek yeni indirdiğiniz bu klasörü seçin.

---

## 🌿 Görev 4: Dal (Branch) Açma ve İlk Değişiklik
Ana dosyaları bozmamak için kendimize güvenli bir çalışma alanı (dal) açacağız.

### Yapılacaklar
- [ ] Terminalde yeni bir dal oluşturun ve o dala geçin: `git checkout -b branch_adi`
- [ ] Obsidian'a dönün. Projenin içindeki `Hayvanlar` klasörüne tatlı bir hayvan resmi koyun 🐱.
- [ ] Dosyanın içine kendinizi tanıtan kısa bir yazı ve GitHub profil linkinizi ekleyin.

> [!info] **Araştırılacak Konular**
> Branch (Dal) nedir?

---

## 💾 Görev 5: Kaydetme (Commit)
Yaptığınız bu değişikliği Git'in tarihçesine kalıcı olarak ekleyin.

### Yapılacaklar
- [ ] Terminalde `git status` yazarak Git'in yeni dosyanızı fark ettiğini (kırmızı renkte) görün.
- [ ] Dosyayı "kaydedilecekler" listesine (sahneye) ekleyin: `git add .`
- [ ] Tekrar `git status` yazın ve dosyanın yeşile döndüğünü teyit edin.
- [ ] Değişikliğinizi açıklayıcı bir mesajla kaydedin (commit): `git commit -m "Açıklama"`

> [!tip] **Farkı Anlayın**
> Obsidian'da `Ctrl+S` yapmak dosyayı bilgisayara kaydeder. `git commit` ise dosyanın o anki durumunun bir **fotoğrafını çeker** ve proje tarihçesine ekler.

---

## 🚀 Görev 6: GitHub'a Gönderme ve Pull Request (PR)
Bilgisayarınızdaki değişiklikleri internete gönderip, ana projeye eklenmesi için teklif sunun.

### Yapılacaklar
- [ ] Bilgisayarınızdaki yeni dalı kendi GitHub'ınıza gönderin: `git push -u origin isim-soyisim-notu`
- [ ] (Eğer şifre sorarsa, ekrana çıkan tarayıcı penceresinden GitHub'a giriş yapıp yetki verin).
- [ ] Kendi GitHub hesabınızdaki repo sayfanıza gidin. Açık yeşil renkte **"Compare & pull request"** butonunu göreceksiniz; ona tıklayın.
- [ ] Çıkan sayfada başlığa istediğiniz bir "Açıklama" yazın.
- [ ] **"Create pull request"** butonuna basarak ana projenin sahibine değişikliğinizi gönderin.

🎉 **Tebrikler!** Açık kaynaklı bir projeye ilk katkınızı (Pull Request) yapmış oldunuz!

---
#git #github #version-control #obsidian #pull-request