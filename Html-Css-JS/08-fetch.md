---
tags: [html, css, javascript, asama-3]
ders: 8
konu: "fetch() — Frontend'in Backend'e Konuştuğu Nokta"
---

# Ders 8: fetch() — Frontend'in Backend'e Konuştuğu Nokta

## 1. Konunun Amacı

AŞAMA 3'ün en önemli dersi. `fetch()`, JavaScript'in HTTP isteği atmak için kullandığı yerleşik fonksiyondur — Python'daki `requests` kütüphanesinin karşılığı.

## 2. Teori

### Temel Kullanım

```javascript
fetch("https://api.github.com/repos/python/cpython")
    .then(response => response.json())
    .then(data => console.log(data));
```

Python karşılığı:
```python
import requests
response = requests.get(url)
data = response.json()
```

### Neden Asenkron? — Promise Kavramı

`fetch()` anında cevap dönmez. JavaScript tek thread'de çalışır ve bekleme sırasında sayfanın donmasını istemez. Bu yüzden `fetch()`, hemen sonuç değil bir **Promise** (söz) döner.

```javascript
let sonuc = fetch("...");
console.log(sonuc);  // Promise { <pending> }
```

`.then()`, Promise sonuçlandığında ne yapılacağını tanımlar:
```javascript
fetch(url)
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.log("Hata:", error));
```

İki `.then()` olmasının sebebi: `response.json()` da zaman alabileceği için ayrıca bir Promise döner.

### async/await — Promise'i Okunabilir Hale Getirmek

```javascript
async function veriGetir() {
    let response = await fetch(url);
    let data = await response.json();
    console.log(data);
}
veriGetir();
```

- **`async`** → fonksiyon içinde `await` kullanılabilir, fonksiyon kendisi bir Promise döner.
- **`await`** → "bu işlemin sonuçlanmasını bekle, sonra devam et."

### POST İsteği Atmak

```javascript
async function kullaniciOlustur() {
    let response = await fetch("http://127.0.0.1:8000/users", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ isim: "Ahmet", email: "ahmet@mail.com" })
    });
    let data = await response.json();
    console.log("Backend'den gelen:", data);
}
```

- **`method: "POST"`** → bkz. [[../web-http-temelleri/06-http-methods|HTTP Methods]]
- **`headers`** → bkz. [[../web-http-temelleri/07-http-headers|HTTP Headers]]
- **`body: JSON.stringify(...)`** → JS object'ini JSON string'ine çevirir (Python'daki `json.dumps()` karşılığı, bkz. [[../web-http-temelleri/11-json|JSON]])
- **`await response.json()`** → gelen JSON'u tekrar JS object'ine çevirir

## 3. KRİTİK TUZAK: `fetch()` Hata Fırlatmaz!

**`fetch()`, Python'daki `requests`'ten farklı olarak, `404` veya `500` gibi hata status code'larında `catch` bloğuna düşmez.** Sadece **ağ bağlantısı tamamen koptuğunda** hata fırlatır. Server "hatalı" bir cevap (`404`, `500`) dönse bile, teknik olarak bir HTTP cevabı geldiği için `fetch()` bunu **başarılı** sayar.

```javascript
// YANLIŞ varsayım:
try {
    let response = await fetch(url);  // 404 dönse bile buraya düşmez!
    let data = await response.json();
} catch (error) {
    console.log("404 olsa buraya düşer sanılıyor ama düşmez");
}

// DOĞRU yaklaşım:
let response = await fetch(url);
if (!response.ok) {  // response.ok, status 200-299 arasıysa true
    console.log("Hata! Status:", response.status);
} else {
    let data = await response.json();
}
```

Bu sonucu backend tasarımına yansıt: hata durumlarında sadece status code değil, body içinde de `{"detail": "..."}` gibi anlamlı bir açıklama dönmek gerekir (FastAPI'nin `HTTPException` mekanizması, AŞAMA 4'te işlenecek).

## 4. Gerçek Dünya Bağlantısı — Form + fetch Birlikte

```html
<form id="kayit-formu">
    <input type="text" name="isim" id="isim">
    <input type="email" name="email" id="email">
    <button type="submit">Kayıt Ol</button>
</form>

<script>
document.getElementById("kayit-formu").addEventListener("submit", async (event) => {
    event.preventDefault();

    let isim = document.getElementById("isim").value;
    let email = document.getElementById("email").value;

    let response = await fetch("http://127.0.0.1:8000/users", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ isim: isim, email: email })
    });

    if (response.ok) {
        let data = await response.json();
        console.log("Başarılı:", data);
    } else {
        console.log("Hata! Status code:", response.status);
    }
});
</script>
```

Bu JavaScript, FastAPI tarafında şu endpoint'e istek atar:
```python
@app.post("/users")
def create_user(user: KullaniciModeli):
    return {"message": "Kullanıcı oluşturuldu", "isim": user.isim}
```

İki taraf **URL, method ve veri formatı** konusunda anlaşmak zorundadır — bu anlaşma API'nin sözleşmesidir (bkz. [[../web-http-temelleri/13-api|API Nedir?]]).

## Kritik Nokta

- POST ile yeni kaynak oluşturulduğunda dönen status code `201 Created` olmalıdır (bkz. [[../web-http-temelleri/08-http-status-codes|HTTP Status Codes]]).
- `response.ok` kontrolü, `fetch()` kullanan her frontend kodunda mutlaka yapılmalıdır — aksi halde hata durumları sessizce "başarılı" gibi işlenir.

## İlgili Notlar
- [[07-dom-ve-events|DOM ve Events]]
- [[06-javascript-temelleri|JavaScript Temelleri]]
- [[03-html-forms-inputs|HTML Forms ve Inputs]]
- [[../web-http-temelleri/06-http-methods|HTTP Methods]]
- [[../web-http-temelleri/08-http-status-codes|HTTP Status Codes]]
- [[../web-http-temelleri/11-json|JSON]]
- [[../web-http-temelleri/13-api|API Nedir?]]
