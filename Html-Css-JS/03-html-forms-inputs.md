---
tags: [html, css, javascript, asama-3]
ders: 3
konu: "HTML Forms ve Inputs — Backend'e Giden Kapı"
---

# Ders 3: HTML Forms ve Inputs — Backend'e Giden Kapı

## 1. Konunun Amacı

Backend developer için HTML'in en kritik parçası. Bir kullanıcının doldurduğu her form, FastAPI backend'ine bir HTTP isteği olarak gider.

## 2. Teori

### Form Elementi ve Temel Attribute'ları

```html
<form action="/kullanici-olustur" method="POST">
    <input type="text" name="isim">
    <button type="submit">Gönder</button>
</form>
```

- **`action`** → verinin gönderileceği URL (FastAPI endpoint'i)
- **`method`** → hangi HTTP method'u (bkz. [[../web-http-temelleri/06-http-methods|HTTP Methods]])

**GET ile gönderim:** Veri URL'in sonuna eklenir (query string): `/ara?q=python`. Hassas olmayan işlemler için (URL, tarayıcı geçmişinde/loglarda görünür).

**POST ile gönderim:** Veri body'de gider, URL'de görünmez. Şifre gibi hassas veriler için kullanılır (HTTPS olmadan yine düz metindir, bkz. [[../web-http-temelleri/05-https|HTTPS]]).

### Input Türleri

```html
<input type="text" name="isim">
<input type="email" name="email">
<input type="password" name="sifre">
<input type="number" name="yas">
<input type="checkbox" name="kabul_ediyorum">
<input type="radio" name="cinsiyet" value="erkek">
<input type="date" name="dogum_tarihi">
<input type="file" name="belge">
```

```html
<select name="sehir">
    <option value="istanbul">İstanbul</option>
</select>
<textarea name="mesaj" rows="4"></textarea>
```

### Form Gönderildiğinde Ne Olur?

```html
<form action="/giris" method="POST">
    <input type="text" name="kullanici_adi" value="ahmet123">
    <input type="password" name="sifre" value="gizli123">
</form>
```

Gönderildiğinde tarayıcı şu isteği oluşturur:
```
POST /giris HTTP/1.1
Content-Type: application/x-www-form-urlencoded

kullanici_adi=ahmet123&sifre=gizli123
```

Backend, veriyi `name` değerleriyle eşleşen anahtarlarla okur.

## 3. Gerçek Dünya Bağlantısı

```python
from pydantic import BaseModel

class KayitFormu(BaseModel):
    isim: str
    email: str
    sifre: str
```

Buradaki `isim`, `email`, `sifre` isimleri **HTML formundaki `name` attribute'larıyla birebir eşleşmelidir**.

**Frontend-backend isimlendirme uyumu:** Python (backend) genelde `snake_case`, JavaScript (frontend) genelde `camelCase` kullanır. Sorun, iki taraf **anlaşmadığında** çıkar. Çözümler:
1. Backend, Pydantic `Field(alias=...)` ile dışa `camelCase` gösterir, içeride `snake_case` kullanır.
2. Ekip, tek bir standarda (genelde snake_case) uymayı kabul eder.

## Kritik Nokta — GET ile Form Gönderme Riski

`method="GET"` ile şifre gibi bir alan gönderilirse, URL'in sonunda **şifre dahil tüm veriler düz metin olarak görünür** — tarayıcı geçmişinde, sunucu loglarında saklanabilir. Bu yüzden login/kayıt formları her zaman `POST` kullanır.

## İlgili Notlar
- [[02-html-attributes-semantic|HTML Attributes ve Semantic HTML]]
- [[../web-http-temelleri/06-http-methods|HTTP Methods]]
- [[../web-http-temelleri/11-json|JSON]]
- [[08-fetch|fetch()]]
