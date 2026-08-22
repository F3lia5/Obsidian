---
tags: [git, github, asama-1]
ders: 4
konu: "Rebase Nedir?"
---

# Ders 4: Rebase Nedir?

## 1. Konunun Amacı

Merge, iki dalı olduğu gibi birleştirince bazen ekstra bir "merge commit" oluşur ve geçmiş dallanıp karmaşıklaşır. Rebase, aynı sonucu daha temiz, düz bir çizgi halinde elde etmenin yoludur.

## 2. Teori

Merge iki dalı olduğu gibi birleştirir (geçmiş dallı kalır). Rebase ise feature branch'indeki commit'leri, sanki en baştan `main`'in en son noktasından başlamış gibi **yeniden yazar**.

```
Rebase öncesi:
main:     A---B---C---F
                    \
feature:             D---E

Rebase sonrası (feature branch'indeyken git rebase main):
main:     A---B---C---F
                        \
feature:                 D'---E'
```

D ve E, D' ve E' oldu — bunlar yeni commit'lerdir. Aynı içeriğe sahipler ama farklı commit hash'lerine sahipler, çünkü ebeveyn commit'leri değişti (artık F'nin üzerine kuruluyorlar, eski C'nin değil).

Sonra `main`'e geçip `feature`'ı merge edersen fast-forward olur ve dümdüz bir geçmiş elde edersin — merge commit'i olmadan.

## 3. KRİTİK KURAL

**Rebase, commit geçmişini yeniden yazar.** Bu yüzden asla başkalarıyla paylaşılmış (push edilmiş, ortak kullanılan) bir branch'i rebase etme. Sadece kendi local, henüz paylaşmadığın branch'lerinde kullan. Aksi halde ekip arkadaşlarının geçmişiyle seninki çakışır, büyük kaos çıkar.

## 4. Gerçek Dünya Bağlantısı

Tipik kullanım: `feature/login` branch'inde günlerdir çalışıyorsun, bu sürede `main` çok kez güncellendi. PR açmadan önce:

```bash
git switch feature/login
git rebase main
```

Bu, çalışmanı sanki `main`'in en güncel haliyle başlamışsın gibi yeniden düzenler. PR artık main'in üzerine temiz oturur.

**Interactive rebase** (`git rebase -i`) ile commit'leri birleştirebilir (squash), sırasını değiştirebilir, mesajlarını düzenleyebilirsin — PR açmadan önce geçmişi temizlemek için kullanılır.

## 5. Komutlar

```bash
git switch feature/deneme
git rebase main

# Conflict çıkarsa:
git add <dosya>
git rebase --continue

# Vazgeçmek için:
git rebase --abort

# Son 3 commit'i interaktif düzenle:
git rebase -i HEAD~3
```

## Kritik Nokta

Rebase sonrası commit hash'leri **değişir**, çünkü bunlar teknik olarak yeni commit'lerdir (farklı ebeveyne sahipler). İçerik aynı olsa da Git için bunlar farklı objelerdir.
