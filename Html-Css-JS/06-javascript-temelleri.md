---
tags: [html, css, javascript, asama-3]
ders: 6
konu: "JavaScript Temelleri — Variables, Functions, Arrays, Objects"
---

# Ders 6: JavaScript Temelleri — Variables, Functions, Arrays, Objects

## 1. Konunun Amacı

JavaScript, backend developer için CSS'ten çok daha önemlidir — çünkü frontend'in backend'e nasıl istek attığını (fetch) JavaScript belirler.

## 2. Teori

### Değişkenler

```javascript
let isim = "Ahmet";          // değişebilir
const yas = 30;               // sabit
var eskiYontem = "kullanma";  // eski, artık tercih edilmiyor
```

### Fonksiyonlar

```javascript
function topla(a, b) {
    return a + b;
}

// Arrow function (modern, kısa yazım - fetch() ile çok sık görülür)
const topla = (a, b) => a + b;
```

### Arrays (Python'daki list gibi)

```javascript
let sayilar = [1, 2, 3, 4, 5];

sayilar.push(6);            // sona ekle (Python: append)
sayilar.length;              // uzunluk (Python: len())
sayilar.map(x => x * 2);     // her elemanı dönüştür
sayilar.filter(x => x > 2);  // filtrele
```

(bkz. [[07-Listeler]])

### Objects (Python'daki dict gibi)

```javascript
let kullanici = {
    isim: "Ahmet",
    yas: 30,
    email: "ahmet@mail.com"
};

console.log(kullanici.isim);     // nokta ile erişim
console.log(kullanici["isim"]);  // köşeli parantezle de olur
```

(bkz. [[10-Dictionary]])

**Kritik nokta:** JavaScript object yapısı, [[../web-http-temelleri/11-json|JSON]]'a neredeyse birebir aynıdır — JSON adını "JavaScript Object Notation"dan alır. Tek görünür fark: JSON'da key'ler her zaman **çift tırnak** içindedir (`{"isim": "Ahmet"}`), JS object'inde tırnak zorunlu değildir (`{isim: "Ahmet"}`).

## 3. Gerçek Dünya Bağlantısı

FastAPI'den dönen JSON:
```json
{"isim": "Ahmet", "yas": 30}
```
JavaScript'te otomatik olarak şuna dönüşür:
```javascript
{ isim: "Ahmet", yas: 30 }
```
Backend'in JSON formatı, doğrudan frontend'in JS object'ine karşılık gelir.

## 4. Kod Örneği

```javascript
let kullanicilar = [
    { isim: "Ahmet", yas: 30 },
    { isim: "Ayşe", yas: 25 }
];

let isimler = kullanicilar.map(k => k.isim);          // ["Ahmet", "Ayşe"]
let buyukler = kullanicilar.filter(k => k.yas > 27);  // [{isim: "Ahmet", yas: 30}]
```

## İlgili Notlar
- [[../web-http-temelleri/11-json|JSON]]
- [[07-dom-ve-events|DOM ve Events]]
- [[08-fetch|fetch()]]
