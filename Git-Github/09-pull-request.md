---
tags: [git, github, asama-1]
ders: 9
konu: "Pull Request (PR) ve Code Review Workflow"
---

# Ders 9: Pull Request (PR) ve Code Review Workflow

## 1. Konunun Amacı

Branch'teki değişiklikleri direkt `git merge` ile birleştirmek yerine neden GitHub'da bir "Pull Request" açılır? Çünkü kod, kimse görmeden ana projeye girmemeli.

## 2. Teori

**Pull Request (PR)**: "Benim şu branch'imdeki değişiklikleri, şu branch'e (genelde main) birleştirmek istiyorum, lütfen incele ve onayla" demenin resmi yolu. Tamamen GitHub'ın (Git'in değil) bir özelliğidir.

**PR akışı:**
```
1. git switch -c feature/x
2. Kod yaz, commit et
3. git push -u origin feature/x
4. GitHub'da "Compare & Pull Request" butonuna bas
5. Açıklama yaz, reviewer ata
6. Reviewer inceler, yorum yapar/değişiklik ister/onaylar
7. Onaylanınca "Merge Pull Request" ile main'e birleşir
8. Feature branch genelde silinir
```

**Neden direkt merge etmiyoruz?**
- **Kalite kontrolü**: Başka bir göz, senin göremediğin hataları yakalar.
- **Bilgi paylaşımı**: Ekip birbirinin kodundan haberdar olur.
- **Otomatik kontroller**: PR açıldığında CI/CD (test, lint, build) tetiklenir; testler geçmeden merge edilemez.
- **Geri dönülebilirlik**: PR'lar tarihe kaydedilir, "bu değişiklik neden yapıldı, kim onayladı" izlenebilir kalır.

## 3. Gerçek Dünya Bağlantısı

Ciddi şirketlerde `main` genelde **korumalıdır (branch protection)** — kimse direkt push edemez, sadece PR + en az 1 onay ile değişiklik girebilir.

## 4. Komutlar

```bash
git switch -c feature/readme-guncelle
git add README.md
git commit -m "docs: readme'ye proje açıklaması eklendi"
git push -u origin feature/readme-guncelle
# ardından GitHub'da "Compare & pull request" butonuna tıklanır
```

## Kritik Nokta — Gerçek Örnekten

Merge stratejisi olarak **Squash and merge** seçildiğinde:

```
$ git log --oneline
ab925a5 (HEAD -> main, origin/main, origin/HEAD) docs: readme'ye proje aciklamasi eklendi (#1)
cd2df2e Add initial content to README.md
50fa94f first commit
```

- `(#1)` → GitHub'ın otomatik eklediği PR numarası; geçmiş izlenebilir kalır.
- Feature branch'te birden fazla commit olsaydı bile, squash sonrası main'de **tek bir temiz commit** olarak görünür.
- Bunun bedeli: orijinal commit detayları main log'unda görünmez, ama GitHub'daki PR geçmişinde saklı kalır.

**`less` pager hatası (sistemsel not):** `git log` çıktısı için Git varsayılan olarak `less` pager'ı kullanır. Kurulu değilse:
```bash
git --no-pager log --oneline          # geçici çözüm
git config --global core.pager cat    # kalıcı çözüm
sudo apt install less                 # gerçek çözüm
```

---

## 🔗 İlgili Dersler

- [[02-branch|Branch]]
- [[03-merge|Merge]]
- [[05-conflict-cozme|Conflict Çözme]]
- [[06-remote-branch-tracking|Remote Branch Tracking]]
- [[08-fork|Fork]]
- [[10-commit-mesajlari|İyi Commit Mesajı]]
