---
tags: [html, css, javascript, asama-3]
ders: 5
konu: "CSS — Flexbox, Grid ve Responsive Design (Özet)"
---

# Ders 5: CSS — Flexbox, Grid ve Responsive Design (Özet)

## 1. Konunun Amacı

Backend developer için derinlemesine gerekli değil — sadece bir frontend developer'ın bu terimleri kullandığında ne demek istediğini anlamak yeterli.

## 2. Teori (Özet)

**Flexbox** — Elementleri **tek boyutta** (satır ya da sütun) esnek hizalamak için:
```css
.container {
    display: flex;
    justify-content: center;
    align-items: center;
}
```
Butonları yan yana dizmek, navbar hizalamak gibi işler için kullanılır.

**Grid** — Elementleri **iki boyutta** (satır VE sütun) düzenlemek için:
```css
.container {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 10px;
}
```
Ürün listesi, dashboard kart düzenleri için kullanılır.

**Responsive Design** — Sitenin farklı ekran boyutlarında (telefon, tablet, masaüstü) düzgün görünmesi. `@media` kuralı ile yapılır:
```css
@media (max-width: 600px) {
    .container { flex-direction: column; }
}
```

## 3. Gerçek Dünya Bağlantısı

Nadiren API tasarımını etkiler (örn. mobil için farklı sayfalama/veri boyutu gerekebilir), ama asıl önemlisi bir frontend arkadaşla konuşurken bu kelimelerin "görünüm meselesi, backend'i ilgilendirmiyor" olduğunu ayırt edebilmektir.

## İlgili Notlar
- [[04-css-selectors-box-model|CSS Selectors ve Box Model]]
