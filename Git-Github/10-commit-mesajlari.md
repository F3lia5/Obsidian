---
tags: [git, github, asama-1]
ders: 10
konu: "İyi Commit Mesajı Yazma"
---

# Ders 10: İyi Commit Mesajı Yazma

## 1. Konunun Amacı

İyi commit mesajı, geleceğe bıraktığın bir nottur. Kötü mesajlar (`fix`, `update`, `asdasd`, `çalışıyor artık`) 6 ay sonra hiçbir işe yaramaz.

## 2. Teori — Conventional Commits

Endüstride en yaygın standart. Format:
```
<tip>(<kapsam>): <kısa açıklama>

<opsiyonel detaylı açıklama>
```

**En çok kullanılan tipler:**
- `feat`: yeni bir özellik eklendi
- `fix`: bir hata düzeltildi
- `docs`: sadece dokümantasyon değişikliği
- `refactor`: davranış değişmeden kodun iç yapısı yeniden düzenlendi
- `test`: test eklendi/düzenlendi
- `chore`: bakım işi (bağımlılık güncelleme, config değişikliği)
- `style`: kod formatlama / görünüm değişikliği (mantık değişmedi — örn. buton rengi)

**Örnekler:**
```
feat(auth): JWT ile login endpoint eklendi
fix(database): kullanıcı silme işleminde foreign key hatası düzeltildi
refactor(voice): ses tanıma fonksiyonu ayrı modüle taşındı
style(login): buton rengi değiştirildi
chore: requirements.txt güncellendi
```

## 3. Kurallar

1. **Ne** yaptığını söyle, **nasıl** yaptığını değil (kod zaten "nasıl"ı gösteriyor).
2. Tutarlı bir kip kullan (ekip neyi seçtiyse ona uy).
3. İlk satırı kısa tut (50-72 karakter civarı), gerekirse boş satır bırakıp detay ekle.
4. **Bir commit, bir amaç** taşımalı. Mesajda "ve ayrıca" geçiyorsa bu genelde iki ayrı commit gerektiğinin işaretidir.

## 4. Gerçek Dünya Bağlantısı

Conventional Commits sadece okunabilirlik için değil, **otomasyon** için de kullanılır:
- `feat`/`fix` commit'lerinden otomatik CHANGELOG oluşturulabilir.
- Semantic versioning (v1.2.3) otomatik hesaplanabilir: `feat` → minor artış, `fix` → patch artış, breaking change → major artış.
- CI/CD pipeline'ları commit tipine göre farklı davranabilir.

## 5. Komutlar

```bash
git commit -m "feat(voice): mikrofon giriş seviyesi ayarlanabilir yapıldı"

# Çok satırlı, detaylı commit:
git commit -m "fix(ollama_response): boş yanıt döndüğünde çökme engellendi

Ollama API bazen boş string döndürüyordu, bu JSON parse
hatasına sebep oluyordu. Şimdi boş yanıt kontrolü eklendi."
```

## Kritik Nokta — Örnek Ayrıştırma

*"login sayfasındaki buton rengini değiştirdim ve ayrıca kullanıcı adı boşsa hata veren bug'ı düzelttim"*

Bu iki farklı iş: görünüm değişikliği + hata düzeltme. İki ayrı commit olmalı:
```
style(login): buton rengi değiştirildi
fix(login): kullanıcı adı boş olduğunda hata veren bug düzeltildi
```
Not: Buton rengi `refactor` değil `style`'dır — davranış değişmiyor, sadece görünüm değişiyor. `refactor`, davranışı aynı bırakıp kodun iç yapısını değiştirmektir.

---

## 🔗 İlgili Dersler

- [[01-git-nedir-ve-neden-kullanilir|Git Nedir?]]
- [[09-pull-request|Pull Request]]
- [[11-log-diff-stash|git log / diff / stash]]
- [[12-reset-vs-revert|reset vs revert]]
