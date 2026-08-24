---
tags: [git, github, asama-1]
ders: 7
konu: "Fetch vs Pull"
---

# Ders 7: Fetch vs Pull

## 1. Konunun Amacı

`git pull` iki farklı işlemi birleştiriyor. Bunu bilmemek bazen beklenmedik merge'lere/conflict'lere sebep olur.

## 2. Teori

**`git fetch`**: Remote'taki (GitHub'daki) yeni commit'leri indirir, ama **local branch'ine hiç dokunmaz**. Sadece `origin/main`'i (remote-tracking branch) günceller.

**`git pull`**: İki adımı arka arkaya yapar:
```
git pull = git fetch + git merge origin/main
```

```
Fetch sonrası:
main:          A---B---C            (senin local'in, değişmedi)
origin/main:   A---B---C---D---E    (güncellendi, senin main'in hâlâ eski)

Pull sonrası (fetch + merge):
main:          A---B---C---D---E    (artık local'in de güncel)
origin/main:   A---B---C---D---E
```

**Fetch neden ayrı bir komut olarak var?** Bazen remote'ta neler değiştiğini önce görmek, otomatik birleşmeden önce kontrol etmek istersin:

```bash
git diff main origin/main    # ne değişmiş, gör
git log main..origin/main    # hangi commit'ler gelmiş, gör
```

## 3. Gerçek Dünya Bağlantısı

Deneyimli geliştiriciler direkt `git pull` yerine önce `git fetch` yapıp neyin geldiğine bakmayı tercih eder — özellikle commit edilmemiş değişiklik varken. `pull` otomatik merge yaptığı için sürpriz conflict/merge commit çıkabilir.

`git pull --rebase` da yaygındır: fetch + merge yerine fetch + rebase yapar, gereksiz merge commit'leri oluşmaz.

## 4. Komutlar

```bash
git fetch origin              # sadece indir, dokunma
git log HEAD..origin/main     # neler gelmiş, gör
git merge origin/main         # sen karar ver, birleştir

# vs.

git pull                      # fetch + merge otomatik
git pull --rebase             # fetch + rebase otomatik
```

## Kritik Nokta — Gerçek Örnekten

```
$ git fetch
   50fa94f..cd2df2e  main       -> origin/main

$ git status
Your branch is behind 'origin/main' by 1 commit, and can be fast-forwarded.

$ git pull
Updating 50fa94f..cd2df2e
Fast-forward
```

`fetch` sadece `origin/main`'i güncelledi (local `main` hâlâ eski). `git status` bunu "behind" diyerek doğruladı. `git pull` ise fast-forward ile local `main`'i de güncel hale getirdi.

**Özet: fetch = bilgi al, pull = bilgi al + uygula.**

---

## 🔗 İlgili Dersler

- [[06-remote-branch-tracking|Remote Branch Tracking]]
- [[04-rebase|Rebase]]
- [[05-conflict-cozme|Conflict Çözme]]
- [[09-pull-request|Pull Request]]
