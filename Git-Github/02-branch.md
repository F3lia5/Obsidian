---
tags: [git, github, asama-1]
ders: 2
konu: "Branch Nedir?"
---

# Ders 2: Branch Nedir?

## 1. Konunun Amacı

Ana hat (main) üzerinde çalışırken yeni bir özellik eklemek istiyorsun ama bu özellik yarım kalırsa veya bug'lı çıkarsa ana kodun bozulmasını istemiyorsun. Branch bu izolasyonu sağlar.

## 2. Teori

Branch, commit geçmişinin bağımsız bir dalıdır. Aslında bir branch, belirli bir commit'i işaret eden hafif bir **pointer**'dan başka bir şey değildir — dosyaların kopyası alınmaz.

```
main:     A---B---C
                    \
feature:             D---E
```

`main`, C'de dururken `feature`, D ve E ile bağımsız devam eder. `main` üzerinde hiçbir şey bozulmaz.

**Neden var?**
- Yeni özellik geliştirirken ana kodu bozmamak
- Paralel işler yürütebilmek
- Deneysel kod yazıp işe yaramazsa branch'i silip main'e hiç dokunmamış olmak

## 3. Gerçek Dünya Bağlantısı

Tipik yapı:
- `main` → her zaman çalışır durumda, production kodu
- `develop` → geliştirmenin birleştiği ara branch
- `feature/login-sistemi` → her özellik kendi branch'inde
- `hotfix/payment-bug` → production'da acil düzeltme

Bir developer asla direkt `main` üzerinde kod yazmaz.

## 4. Komutlar

```bash
git branch feature/notlar-ekle       # branch oluştur
git checkout feature/notlar-ekle     # o branch'e geç
git checkout -b feature/notlar-ekle  # oluştur + geç (kısayol)
git switch -c feature/notlar-ekle    # modern komut (Git 2.23+)
git branch                           # branch listesi
```

## Kritik Nokta

Branch oluşturduğunda Git dosyaların **kopyasını almaz** — sadece mevcut commit'e işaret eden yeni bir pointer oluşturur. Bu yüzden branch oluşturmak çok "ucuz" (hafif, hızlı) bir işlemdir.

`main`'e geri döndüğünde başka bir branch'te commit'lediğin dosyaları göremezsin, çünkü o commit henüz `main`'in tarihçesine hiç girmemiştir.

---

## 🔗 İlgili Dersler

- [[01-git-nedir-ve-neden-kullanilir|Git Nedir?]]
- [[03-merge|Merge]]
- [[04-rebase|Rebase]]
- [[05-conflict-cozme|Conflict Çözme]]
- [[06-remote-branch-tracking|Remote Branch Tracking]]
- [[09-pull-request|Pull Request]]
