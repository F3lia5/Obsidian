---
tags: [git, github, asama-1]
ders: 3
konu: "Merge Nedir?"
---

# Ders 3: Merge Nedir?

## 1. Konunun Amacı

Bir feature branch'inde çalışmayı bitirdin, artık bu değişikliği `main`'e geri kazandırmak istiyorsun. Bu birleştirme işlemine merge denir.

## 2. Teori — İki Merge Türü

### a) Fast-forward merge
`main`, sen `feature` üzerinde çalışırken hiç değişmediyse, Git basitçe `main`'in pointer'ını `feature`'ın son commit'ine kaydırır. Yeni commit oluşturulmaz.

```
Önce:
main:     A---B---C
                    \
feature:             D---E

Sonra (fast-forward):
main:     A---B---C---D---E
```

### b) 3-way merge (gerçek merge)
`main` da sen çalışırken ilerlediyse, Git iki dalı birleştiren yeni bir commit oluşturur — **merge commit**. Bu, iki ebeveyni (parent) olan tek commit türüdür.

```
main:     A---B---C-------F  (F = merge commit)
                    \     /
feature:             D---E
```

Git, iki branch'in ortak atasını (C) bulur, değişiklikleri karşılaştırır ve otomatik birleştirir. Aynı satırda iki taraf da farklı değişiklik yaptıysa **conflict** oluşur.

## 3. Gerçek Dünya Bağlantısı

GitHub'da "Merge Pull Request" butonu bu işlemi tetikler. Üç yaygın strateji:
- **Merge commit** — geçmiş korunur, dallanma görünür kalır.
- **Squash and merge** — feature branch'teki tüm commit'ler tek bir commit'e sıkıştırılıp main'e eklenir. Ana branch'in geçmişi temiz kalır; feature branch'teki dağınık "wip" commit'leri main'de görünmez, sadece GitHub'daki PR geçmişinde kalır.
- **Rebase and merge** — geçmişi düzleştirir (bkz. Ders 4).

## 4. Komutlar

```bash
git switch main
git merge feature/deneme
```

## Kritik Nokta

Fast-forward mı yoksa gerçek merge mi olacağı, `main`'in senin çalışman sırasında değişip değişmediğine bağlıdır. Değişmediyse fast-forward, değiştiyse merge commit (veya conflict) oluşur.

---

## 🔗 İlgili Dersler

- [[02-branch|Branch]]
- [[04-rebase|Rebase]]
- [[05-conflict-cozme|Conflict Çözme]]
- [[09-pull-request|Pull Request]]
- [[12-reset-vs-revert|Reset vs Revert]]
