---
tags: [html, css, javascript, asama-3]
ders: 2
konu: "HTML Attributes ve Semantic HTML"
---

# Ders 2: HTML Attributes ve Semantic HTML

## 1. Konunun Amacı

Attribute'ların ne işe yaradığını ve semantic (anlamlı) HTML kullanmanın önemini bilmek, okunabilir ve erişilebilir sayfalar için gereklidir. Backend developer için özellikle `name` attribute'u kritiktir.

## 2. Teori

### Attribute Nedir?

Elemente ek bilgi/davranış katan, açılış etiketinin içine yazılan anahtar-değer çiftidir.

```html
<a href="https://example.com" target="_blank">Git</a>
<input type="email" name="kullanici_email" placeholder="E-posta gir" required>
```

- `href` → linkin adresi
- `target="_blank"` → yeni sekmede aç
- `type="email"` → input türü, tarayıcı otomatik doğrulama yapar
- **`name`** → **kritik**: form gönderildiğinde veri backend'e bu isimle gider
- `placeholder` → ipucu metni
- `required` → doldurulmadan form gönderilemez

**`name` attribute'u olmayan bir input, form gönderildiğinde backend'e hiç gitmez** — `id` sadece tarayıcı içi (CSS/JS) referans sağlar, sunucuya giden veriyle ilgisi yoktur.

### Semantic HTML Nedir?

Elementlerin görevini isimleriyle anlatan etiketleri kullanmaktır.

```html
<!-- Semantic olmayan (eski/kötü) -->
<div class="header">...</div>
<div class="nav">...</div>

<!-- Semantic (anlamlı) -->
<header>...</header>
<nav>...</nav>
<main>...</main>
<article>...</article>
<section>...</section>
<footer>...</footer>
```

**Neden önemli?**
1. **Erişilebilirlik**: Ekran okuyucular `<nav>` gördüğünde "burası navigasyon" diye anons eder; `<div class="nav">` bunu anlayamaz.
2. **SEO**: Arama motorları semantic etiketleri kullanan sayfaları daha iyi anlar.
3. **Okunabilirlik**: `<div class="wrapper-2">` yerine `<article>` görmek çok daha anlaşılırdır.

Not: Semantic olmayan HTML kullanmak **görsel** olarak fark yaratmaz (tarayıcı ikisini de benzer render eder), sadece **anlam** kaybolur — bundan etkilenen taraf backend değil, ekran okuyucular/SEO/kod okunabilirliğidir.

## 3. `<button>` Tuzağı

`<button>` etiketinin `type` belirtilmezse **varsayılan davranışı `type="submit"`dir** — form içindeki herhangi bir buton, type belirtilmezse otomatik olarak formu gönderir. Bu, "iptal"/"sil" gibi butonlarda unutulduğunda beklenmedik POST isteklerine yol açan yaygın bir bug kaynağıdır.

```html
<button>Gönder</button>              <!-- type="submit" gibi davranır -->
<button type="button">İptal</button> <!-- hiçbir şey yapmaz -->
```

## 4. Gerçek Dünya Bağlantısı

```html
<form>
    <label for="isim">İsim:</label>
    <input type="text" id="isim" name="isim" required>
    <label for="email">E-posta:</label>
    <input type="email" id="email" name="email" required>
    <button type="submit">Gönder</button>
</form>
```

Bu form gönderildiğinde backend'e `isim` ve `email` isimli iki veri gider — `name` attribute'ları sayesinde.

## İlgili Notlar
- [[01-html-nedir-temel-yapi|HTML Nedir?]]
- [[03-html-forms-inputs|HTML Forms ve Inputs]]
