---
tags: [git, github, asama-1]
ders: 5
konu: "Conflict Nasıl Oluşur ve Çözülür?"
---

# Ders 5: Conflict Nasıl Oluşur ve Çözülür?

## 1. Konunun Amacı

Merge veya rebase sırasında Git bazen otomatik birleştiremez ve karar vermeni ister. Buna **conflict (çakışma)** denir. Gerçek ekip çalışmasında kaçınılmazdır.

## 2. Teori

Conflict, Git iki branch'i birleştirirken **aynı dosyanın aynı satırında** iki farklı değişiklik görürse oluşur. Git hangisinin doğru olduğuna karar veremez, sana bırakır.

Örnek: `main`'de bir satır `"Merhaba"` iken `feature`'da aynı satır `"Selam"` olmuş. Git dosyanın içine şu işaretleri koyar:

```
<<<<<<< HEAD
Merhaba
=======
Selam
>>>>>>> feature/deneme
```

- `<<<<<<< HEAD` ile `=======` arası: bulunduğun branch'teki hal (genelde main)
- `=======` ile `>>>>>>> feature/deneme` arası: birleştirmeye çalıştığın branch'teki hal

## 3. Çözüm Süreci

1. Dosyayı aç, hangi versiyonu (veya birleşimini) istediğine karar ver.
2. `<<<<<<<`, `=======`, `>>>>>>>` işaretlerini elle sil.
3. Dosyanın son, temiz halini bırak.
4. `git add <dosya>` ile "bu conflict'i çözdüm" de.
5. Merge içindeysen `git commit`, rebase içindeysen `git rebase --continue`.

## 4. Gerçek Dünya Bağlantısı

İki geliştirici aynı fonksiyonu/config dosyasını aynı anda düzenlerse conflict kaçınılmazdır. Deneyimli takımlar bunu azaltmak için:
- Küçük, sık commit ve pull yaparlar (uzun süre branch'te kalmazlar)
- Dosyaları modüler tutarlar (herkes farklı dosyalarda çalışsın)

Ama tamamen ortadan kaldırılamaz — conflict çözmek günlük iş akışının doğal bir parçasıdır.

## 5. Komutlar

```bash
git status    # hangi dosyalarda conflict var
git diff      # conflict işaretlerini gör
# dosyayı elle düzenle
git add dosya.txt
git commit    # merge conflict'ini kapatır
```

## Kritik Nokta

`git status`, conflict sırasında hangi dosyaların çakıştığını açıkça listeler ("both modified" gibi ifadelerle) — panik yapmadan önce her zaman ilk bakılacak yer burasıdır.
