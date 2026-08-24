---
tags: [git, github, asama-1]
ders: 12
konu: "reset vs revert"
---

# Ders 12: `reset` vs `revert`

## 1. Konunun Amacı

Yanlış bir commit attın, geri almak istiyorsun. Bu iki komutu (`reset`, `revert`) karıştırmak, özellikle paylaşılmış branch'lerde ciddi kaosa yol açabilir. Git'in en tehlikeli konusu tam olarak burasıdır.

## 2. Teori

### `git reset` — Geçmişi siler / yeniden yazar

Branch pointer'ını geçmişte bir noktaya geri sarar, sanki o commit'ler hiç olmamış gibi. Üç modu var:

```bash
git reset --soft HEAD~1    # commit'i geri al, değişiklikler staging area'da kalsın
git reset --mixed HEAD~1   # commit'i geri al, değişiklikler working tree'de kalsın (varsayılan)
git reset --hard HEAD~1    # commit'i geri al, değişiklikleri de tamamen SİL
```

```
Önce:  A---B---C  (HEAD -> main)
Sonra (reset HEAD~1): A---B  (HEAD -> main)   → C artık yok
```

### `git revert` — Geçmişi korur, üstüne ekler

Geçmişi silmez; o commit'in yaptığı değişikliği tersine çeviren **yeni bir commit** oluşturur.

```
Önce:  A---B---C  (HEAD -> main)
Sonra (revert C): A---B---C---C'  (C' = C'nin tam tersi değişiklik)
```

## 3. KRİTİK KARŞILAŞTIRMA VE ALTIN KURAL

| | `reset` | `revert` |
|---|---|---|
| Geçmişi | Siler / yeniden yazar | Korur, üstüne ekler |
| Paylaşılmış (push edilmiş) branch'te güvenli mi? | ❌ Hayır | ✅ Evet |
| Ne zaman kullanılır | Henüz push etmediğin, sadece kendine ait local commit'ler | Zaten push edilmiş, başkalarının da çektiği commit |

**Altın kural (rebase ile aynı mantık):** Push ettiğin, paylaştığın geçmişi asla yeniden yazma. `reset --hard` + `git push --force` ile geçmişi silip tekrar push etmeye çalışırsan, ekip arkadaşlarının local'indeki geçmiş seninkiyle uyuşmaz hale gelir.

## 4. Gerçek Dünya Bağlantısı

- **`reset`**: "Az önce yanlışlıkla commit attım, henüz push etmedim." → `git reset --soft HEAD~1` ile commit'i geri alır, dosyalar stage'de kalır, düzeltip tekrar commit atarsın.
- **`revert`**: "3 gün önce push edilen bir commit bug'lıymış, ama sonrasında 10 commit daha geldi, geçmişi bozmadan sadece o hatalı değişikliği geri almam lazım." → `git revert <commit-hash>` — yeni bir commit oluşur, herkes normal `pull` ile alır, çakışma olmaz.

Production ortamlarında neredeyse her zaman **`revert` tercih edilir**, çünkü `reset --hard` + force push, canlıda çalışan diğer geliştiricilerin/CI-CD'nin geçmişini bozabilir.

## 5. Komutlar

```bash
# Henüz push etmediğin son commit'i geri al, değişiklikler kalsın
git reset --soft HEAD~1

# Son commit'i TAMAMEN sil (değişiklikler de gitsin) - DİKKATLİ KULLAN
git reset --hard HEAD~1

# Push edilmiş bir commit'i güvenle geri al
git log --oneline           # geri alınacak commit'in hash'ini bul
git revert <commit-hash>
```

## Kritik Nokta — Neden `main`'e Force Push Yasaklanır?

`reset --hard` geçmişi siler. Eğer bu, zaten push edilmiş bir commit üzerinde yapılıp `git push --force` ile GitHub'a gönderilirse, o commit'i çeken (fetch/pull eden) diğer geliştiricilerin local geçmişiyle sunucudaki geçmiş **artık uyuşmaz** hale gelir. Bu yüzden şirketler **branch protection** ile `main`'e force push'u tamamen engeller — geçmiş asla geriye doğru silinemez, sadece `revert` ile ileriye doğru düzeltilebilir.

---

## 🔗 İlgili Dersler

- [[03-merge|Merge]]
- [[04-rebase|Rebase]]
- [[10-commit-mesajlari|İyi Commit Mesajı]]
- [[11-log-diff-stash|git log / diff / stash]]
