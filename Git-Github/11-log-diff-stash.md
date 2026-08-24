---
tags: [git, github, asama-1]
ders: 11
konu: "git log, git diff, git stash"
---

# Ders 11: `git log`, `git diff`, `git stash`

## 1. Konunun Amacı

Bunlar günlük Git kullanımının en çok başvurulan yardımcı araçlarıdır.

## 2. `git log` — Commit Geçmişi

```bash
git log                          # detaylı (yazar, tarih, mesaj)
git log --oneline                # kısa, tek satır
git log --oneline --graph --all  # branch dallanmasını görsel göster
git log -p                       # her commit'in içerik değişikliklerini göster
git log --author="isim"          # belirli birinin commit'leri
git log -- dosya.py              # sadece bir dosyanın geçmişi
```

## 3. `git diff` — Farkları Görme

En kafa karıştıran nokta: **hangi iki durum arasında** olduğu.

```bash
git diff                    # working tree vs staging area (henüz add edilmemiş değişiklikler)
git diff --staged           # staging area vs son commit (add edilmiş, commit edilmemiş)
git diff main feature/x     # iki branch arasındaki fark
git diff HEAD~1 HEAD        # son commit ile bir önceki arasındaki fark
```

## 4. `git stash` — Geçici Rafa Kaldırma

**Senaryo:** `main`'de yarım kalmış değişikliklerin var, ama acil bir bug fix için `hotfix` branch'ine geçmen gerekiyor. Commit etmek istemiyorsun (yarım iş), değişiklikleri kaybetmek de istemiyorsun. `stash`, değişiklikleri geçici bir "rafa kaldırma" alanına koyar, working tree'yi temizler.

```bash
git stash                # değişiklikleri rafa kaldır, working tree temizlenir
git stash list            # raftaki tüm stash'leri listele
git stash pop             # en son stash'i geri getir VE raftan sil
git stash apply           # en son stash'i geri getir AMA rafta bırak (kopyalar)
git stash drop            # bir stash'i rafta sil (geri getirmeden)
```

**`apply` vs `pop` farkı:** `pop`, stash'i geri getirir ve raftan siler (tek kullanımlık). `apply`, geri getirir ama rafta bırakır — aynı stash'i **birden fazla branch'e** uygulamak istediğinde `apply` tercih edilir.

## 5. Gerçek Dünya Bağlantısı

- `git log --author` → "Bu bug'ı kim yazmış, ona sorayım" derken kullanılır.
- `git diff --staged` → Commit atmadan hemen önce "tam olarak neyi commit ediyorum?" diye son kontrol için kritik bir alışkanlıktır.
- `git stash` → "Feature üzerinde yarım işim var, production'da acil hata çıktı, hemen main'e geçip fix yapmam lazım" senaryosunda kullanılır.

## 6. Komut Akışı Örneği

```bash
# Senaryo: main'de yarım iş var, acil branch değiştirmen lazım
git stash
git switch hotfix/acil-bug
# ... fix yap, commit et, push et ...
git switch main
git stash pop   # yarım işin geri geldi
```

---

## 🔗 İlgili Dersler

- [[10-commit-mesajlari|İyi Commit Mesajı]]
- [[12-reset-vs-revert|reset vs revert]]
- [[02-branch|Branch]]
- [[03-merge|Merge]]
- [[05-conflict-cozme|Conflict Çözme]]
