---
tags: [html, css, javascript, asama-3]
ders: 7
konu: "DOM ve Events"
---

# Ders 7: DOM ve Events

## 1. Konunun Amacı

JavaScript'in tarayıcıda "bir şey yapabilmesinin" temeli DOM'dur. Bir kullanıcı bir butona tıkladığında backend'e istek gitmesini tetikleyen mekanizma budur.

## 2. Teori

### DOM (Document Object Model) Nedir?

Tarayıcı, HTML sayfasını yüklediğinde onu bellekte bir **ağaç yapısı** olarak temsil eder:

```
document
  └── html
        ├── head
        │     └── title
        └── body
              ├── h1
              └── div
                    └── p
```

JavaScript bu ağaca erişip değiştirebilir. HTML statikken, DOM üzerinden JS ile **dinamik** hale gelir.

### DOM'a Erişim

```javascript
let baslik = document.getElementById("ana-baslik");
let butonlar = document.querySelectorAll(".buton");  // CSS selector gibi çalışır
let ilkParagraf = document.querySelector("p");

baslik.textContent = "Yeni Başlık";
baslik.innerHTML = "<strong>Kalın Başlık</strong>";
baslik.style.color = "red";
baslik.classList.add("aktif");
```

`getElementById`, benzersiz `id` gerektirir (bkz. [[04-css-selectors-box-model|CSS Selectors]] — id vs class farkı).

### Events (Olaylar)

Kullanıcı bir şey yaptığında (tıklama, yazma, sayfa yükleme) tarayıcı bir **event** tetikler.

```javascript
let buton = document.getElementById("gonder-butonu");

buton.addEventListener("click", () => {
    console.log("Butona tıklandı!");
});
```

**Yaygın event'ler:** `click`, `submit`, `input`, `change`, `DOMContentLoaded`.

### Form Gönderimini JavaScript ile Yakalamak

```javascript
let form = document.getElementById("kayit-formu");

form.addEventListener("submit", (event) => {
    event.preventDefault();  // formun normal (sayfa yenileyen) davranışını DURDUR
    console.log("Form yakalandı, sayfa yenilenmedi.");
    // Buradan sonra fetch() ile backend'e istek atılır
});
```

`event.preventDefault()` olmadan form eski usul sayfayı yeniler ve [[08-fetch|fetch()]] mantığı devreye giremez.

## 3. KRİTİK KAVRAM: DOM Manipülasyonu = SADECE Frontend

DOM manipülasyonu, event dinleme, `getElementById`, `addEventListener` — bunların hepsi **tarayıcıda, kullanıcının bilgisayarında** çalışan JS koduyla yapılır. Backend'in bu sürece hiçbir dahli yoktur, hatta olduğunu bile bilmez.

```
KULLANICININ TARAYICISI (Frontend)
├── HTML → yapı
├── CSS → görünüm
└── JavaScript → davranış (DOM, event'ler, fetch ile istek atma)
        │  (network üzerinden HTTP isteği)
        ▼
SUNUCU (Backend)
└── FastAPI → isteği alır, işler, JSON döner
```

Ayrım örneği:
- "Butona tıklayınca yazı rengi değişti" → **sadece frontend**, backend'in haberi olmaz.
- "Butona tıklayınca veritabanından veri çekildi" → **hem frontend hem backend**: frontend fetch() ile istek atar, backend JSON döner, frontend DOM'a yazar.

## Kritik Nokta

Backend'in devreye girdiği tek an, JavaScript'in `fetch()` ile bir HTTP isteği attığı andır — o zaman veri ağ üzerinden sunucuya gider (bkz. [[08-fetch|fetch()]]).

## İlgili Notlar
- [[06-javascript-temelleri|JavaScript Temelleri]]
- [[04-css-selectors-box-model|CSS Selectors ve Box Model]]
- [[08-fetch|fetch()]]
