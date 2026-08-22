---
tags: [git, github, asama-1]
ders: 6
konu: "Remote Branch Tracking"
---

# Ders 6: Remote Branch Tracking

## 1. Konunun Amacı

`git push` bazen sadece `git push` yazmakla yeterli oluyor, bazen `git push origin main` yazman gerekiyor. Bu farkın sebebi **tracking (izleme) ilişkisi**dir.

## 2. Teori

Local branch'lerin (`main`, `feature/x`) yanında, **remote-tracking branch**'ler vardır: `origin/main` gibi. Bunlar, GitHub'daki branch'lerin senin bilgisayarındaki **son bilinen halinin kopyasıdır** — canlı değil, en son fetch/pull yaptığın andaki görüntüdür.

```
Local:              main
Remote-tracking:    origin/main   (GitHub'daki main'in son bilinen hali)
Gerçek remote:      GitHub'daki main (canlı, görmediğin yeni commit'ler olabilir)
```

**Tracking ilişkisi**: local `main`'in `origin/main`'i "takip ettiği" bilgisidir. Bu ilişki kurulunca:
- `git push` → Git otomatik "bu local main, origin/main'e gitmeli" bilir.
- `git pull` → Git otomatik "origin/main'den çekmeliyim" bilir.
- `git status` → "Your branch is ahead of 'origin/main' by 2 commits" gibi mesajlar bu sayede çıkar.

## 3. Gerçek Dünya Bağlantısı

`git clone` yaptığında, klonlanan `main` otomatik olarak `origin/main`'i track eder.

Ama **yeni bir branch** oluşturup ilk kez push ettiğinde, bu branch henüz GitHub'da yok ve hiçbir şeyi track etmiyor:

```bash
git push -u origin feature/yeni
```

`-u` (`--set-upstream`) "bundan sonra bu local branch, origin'deki bu branch'i track etsin" demektir. Bir kere yapıldıktan sonra sadece `git push` / `git pull` yeterli olur.

## 4. Komutlar

```bash
git branch -vv                          # tracking ilişkilerini gör
git push -u origin feature/yeni-ozellik # ilk push'ta tracking kur
git push                                # sonrasında kısa komut yeterli
git pull
```

## Kritik Nokta — Gerçek Örnekten

`git push -u origin main` çalıştırmadan önce şu üç şeyin **hepsi** olmalı:
1. Local'de commit edilmiş bir branch olmalı
2. Remote tanımlı olmalı (`git remote add origin ...`)
3. Local branch adı, push edilen remote branch adıyla eşleşmeli

Eksik olan herhangi biri şu hatalardan birini verir:
- `src refspec main does not match any` → local branch adı yanlış/yok (örn. `master` iken `main` push etmeye çalışmak)
- `'origin' does not appear to a git repository` → remote hiç tanımlanmamış

Push başarılı olduğunda çıktının son satırı şunu gösterir:
```
branch 'main' set up to track 'origin/main'.
```
Bu, tracking ilişkisinin tam o anda kurulduğunu gösterir.
