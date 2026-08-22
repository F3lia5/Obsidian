---
tags: [git, github, asama-1]
ders: 1
konu: "Git Nedir ve Neden Kullanılır?"
---

# Ders 1: Git Nedir ve Neden Kullanılır?

## 1. Konunun Amacı

Gerçek bir yazılım projesinde şu sorular ortaya çıkar:
- Dün çalışan kodum bugün neden bozuldu? Ne değiştirdim?
- Yeni bir özellik denemek istiyorum ama mevcut çalışan kodu bozmaktan korkuyorum.
- Birlikte çalıştığım biri aynı dosyayı düzenledi, şimdi ne olacak?
- Bilgisayarım bozulursa projem tamamen kaybolur mu?

Git, bu problemlerin hepsini çözmek için var.

## 2. Teori

**Git nedir?**
Git, bir **versiyon kontrol sistemi (version control system)**dir. Projedeki dosyaların zaman içindeki her değişimini kaydeder.

Git olmadan elle versiyonlama böyle görünür:
```
proje.py
proje_v2.py
proje_v2_son.py
proje_v2_son_gercek.py
```
Git bunu otomatik ve akıllı şekilde yapar.

**Git nasıl çalışır (kavramsal)?**
Git, her "kaydedilme anını" (**commit**) bir fotoğraf gibi saklar. Bu sayede:
- Geçmişteki herhangi bir ana geri dönebilirsin.
- İki an arasındaki farkı görebilirsin.
- Aynı anda birden fazla alternatif üzerinde çalışabilirsin (**branch**).
- Başkalarıyla değişiklikleri birleştirebilirsin (**merge**).

## 3. Git vs GitHub

| | Git | GitHub |
|---|---|---|
| Nedir? | Bir yazılım (araç) | Bir web sitesi/servis |
| Nerede çalışır? | Senin bilgisayarında (local) | İnternette (remote) |
| Görevi | Değişiklik geçmişini takip etmek | Repository'leri barındırmak, paylaşmak, işbirliği |
| Analoji | "Undo/redo" tarihçesini tutan motor | O motorun bulut yedeği ve paylaşım platformu |

Git'i GitHub olmadan da (tamamen local) kullanabilirsin. GitHub, projeyi internete taşıyıp paylaşmanı sağlar.

## 4. Gerçek Dünya Bağlantısı

Gerçek bir şirkette:
- Her özellik ayrı bir **branch**'te geliştirilir.
- "Bu hata ne zaman girdi?" diye geçmiş taranabilir.
- Kod, **code review / pull request** ile incelenmeden ana projeye eklenmez.
- Deployment sorun çıkarırsa önceki çalışan versiyona saniyeler içinde dönülür.

## 5. Temel Komutlar

```bash
git init                  # klasörü Git repository'sine çevirir
git status                # değişikliklerin durumunu gösterir
git add dosya.py          # değişikliği staging area'ya ekler
git commit -m "mesaj"     # staging area'daki değişikliği kalıcı kaydeder
```

`git init` çalıştırıldığında klasöre gizli bir `.git` klasörü eklenir — tüm geçmiş, branch bilgisi, commit'ler orada saklanır.

## Özet / Kritik Nokta

- Git init ile bir proje otomatik olarak "takip altına" girmez; dosyaları `add` ile açıkça eklemen gerekir.
- `git status`, working tree (henüz add edilmemiş), staging area (add edilmiş, commit edilmemiş) ve repository (commit edilmiş) arasındaki farkı gösterir.
