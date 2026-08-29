---
tags: [html, css, javascript, asama-3]
ders: 1
konu: "HTML Nedir ve Temel Yapısı"
---

# Ders 1: HTML Nedir ve Temel Yapısı

## 1. Konunun Amacı

Backend developer olarak frontend uzmanı olmak gerekmez, ama FastAPI'nin ürettiği veriyi kimin nasıl kullandığını anlamadan iyi bir API tasarlanamaz. HTML, tarayıcının anladığı yapı dilidir.

## 2. Teori

**HTML (HyperText Markup Language)** bir programlama dili değil, bir **markup (işaretleme) dilidir**. Mantık/hesaplama yapmaz, sadece içeriği yapılandırır.

### Temel HTML İskeleti

```html
<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <title>Sayfa Başlığı</title>
</head>
<body>
    <h1>Merhaba Dünya</h1>
    <p>Bu bir paragraf.</p>
</body>
</html>
```

- **`<!DOCTYPE html>`** → tarayıcıya "bu belge HTML5" der.
- **`<html>`** → tüm belgeyi saran kök element.
- **`<head>`** → görünmeyen ama önemli bilgiler (başlık, karakter kodlaması, CSS/JS bağlantıları) — bu **metadata**dır, sayfa içeriği değildir. `<title>` yanlışlıkla `<body>`'ye taşınırsa tarayıcı sekmesinde görünmez, çünkü görevi tarayıcı sekmesi/arama sonucu/yer imi isimlendirmektir.
- **`<body>`** → kullanıcının gerçekten gördüğü içerik.

### Element Nedir?

```html
<p>Bu bir paragraf.</p>
```
Açılış etiketi + içerik + kapanış etiketi. Bazı elementler self-closing'dir (kapanmaz): `<img>`, `<br>`, `<input>`.

### Nesting (İç İçe Geçme) ve DOM Ağacı

```html
<div>
    <h2>Başlık</h2>
    <p>İçindeki <strong>kalın</strong> bir kelime var.</p>
</div>
```

Bu iç içe geçme, tarayıcının bellekte oluşturduğu **DOM Tree** yapısının temelidir (bkz. [[07-dom-ve-events|DOM ve Events]]).

## 3. `<div>` vs `<span>`

- `<div>` → varsayılan `display: block`, tüm satırı kaplar, alt alta dizilir.
- `<span>` → varsayılan `display: inline`, sadece içeriği kadar yer kaplar, yan yana durabilir.

Bu fark, [[04-css-selectors-box-model|Box Model]] dersindeki `display` kavramının kökenidir.

## 4. Gerçek Dünya Bağlantısı

Backend developer HTML yazmaz ama bir `<form>` elementinin verisi FastAPI backend'ine bir HTTP isteği olarak gider — formun `name` attribute'ları backend'in veriyi hangi isimle alacağını belirler (bkz. [[03-html-forms-inputs|HTML Forms ve Inputs]]). FastAPI bazen `HTMLResponse` ile HTML de döndürebilir.

## 5. Kod Örnekleri

```html
<h1>En büyük başlık</h1>
<h2>Alt başlık</h2>
<p>Paragraf metni.</p>
<a href="https://example.com">Bir bağlantı</a>
<img src="resim.jpg" alt="Resim açıklaması">
<div>Kapsayıcı (container)</div>
<span>Satır içi kapsayıcı</span>
<ul>
    <li>Liste elemanı 1</li>
    <li>Liste elemanı 2</li>
</ul>
```

## İlgili Notlar
- [[02-html-attributes-semantic|HTML Attributes ve Semantic HTML]]
- [[03-html-forms-inputs|HTML Forms ve Inputs]]
- [[04-css-selectors-box-model|CSS Selectors ve Box Model]]
- [[06-javascript-temelleri|JavaScript Temelleri]]
- [[07-dom-ve-events|DOM ve Events]]
- [[08-fetch|fetch()]]
