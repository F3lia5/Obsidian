---
tags: [git, github, asama-1]
ders: 8
konu: "Fork Nedir?"
---

# Ders 8: Fork Nedir?

## 1. Konunun Amacı

Başkasının projesine katkıda bulunmak istiyorsun ama direkt push yetkin yok (açık kaynak, şirket dışı repolar). Fork bu problemi çözer.

## 2. Teori

**Fork**, başka birinin repository'sinin senin kendi GitHub hesabına kopyasını oluşturmaktır. Tamamen GitHub'ın (platformun) bir özelliğidir — Git'in kendisinde "fork" diye bir komut yoktur.

**Clone vs Fork farkı:**
- **Clone**: Bir repo'yu kendi bilgisayarına indirirsin. Repo'nun sahibi değişmez, sadece local kopyan olur.
- **Fork**: Bir repo'nun GitHub'daki kendi hesabına ait bağımsız bir kopyasını oluşturursun. Artık o kopya senindir, kendi remote'un olarak push edebilirsin.

Akış:
```
orijinal-repo (başkasının)
      │  (fork)
      ▼
senin-fork'un (senin GitHub hesabında)
      │  (clone)
      ▼
senin bilgisayarın (local)
```

Kendi fork'unda değişiklik yapıp push edersin (tamamen senin yetkinde). Sonra orijinal projeye katkı sunmak için **Pull Request** açarsın.

## 3. Gerçek Dünya Bağlantısı

Açık kaynak akışı:
1. Repo'yu fork'larsın.
2. Kendi fork'unu clone'larsın.
3. Bir branch açıp değişikliğini yaparsın.
4. Kendi fork'una push edersin.
5. Orijinal projeye Pull Request açarsın.
6. Proje sahipleri review edip kabul ederse kodun ana projeye girer.

Şirket içi projelerde genelde fork kullanılmaz (herkesin zaten repo'ya erişimi vardır), direkt branch + PR akışı kullanılır. Fork daha çok **dışarıdan katkı** senaryosunda devreye girer.

**Önemli nokta:** Direkt push yetkin olsa bile (collaborator olsan bile), bazı ekipler yine de kimsenin direkt `main`'e push etmesini istemez — branch açıp PR üzerinden review alarak merge etmeni ister. Yani yetki push'u serbest bırakmaz, review sürecini atlatmaz.

## 4. Komutlar

Fork'un kendisi GitHub arayüzünde "Fork" butonuyla yapılır. Sonrası:

```bash
git clone git@github.com:senin-kullanici-adin/forklanmis-repo.git
cd forklanmis-repo
git remote add upstream git@github.com:orijinal-sahip/orijinal-repo.git
```

`upstream`: orijinal proje. Senin fork'un `origin` olur. Orijinal projedeki güncellemeleri çekmek için:

```bash
git fetch upstream
git merge upstream/main
```
