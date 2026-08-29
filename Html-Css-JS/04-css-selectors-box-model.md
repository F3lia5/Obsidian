---
tags: [html, css, javascript, asama-3]
ders: 4
konu: "CSS Temelleri — Selectors ve Box Model"
---

# Ders 4: CSS Temelleri — Selectors ve Box Model

## 1. Konunun Amacı

HTML yapıyı oluşturur, CSS o yapıyı görsel olarak biçimlendirir. Backend developer CSS yazmaz ama Box Model gibi kavramları bilmek, bir hatanın frontend mi backend mi kaynaklı olduğunu ayırt etmeye yardımcı olur.

## 2. Teori

### CSS Bağlama

```html
<head>
    <style>
        h1 { color: blue; }
    </style>
</head>
```

`selector { property: value; }` yapısı — hangi elemente, hangi özelliğin, ne değerde uygulanacağını belirtir.

### Selectors

```css
h1 { color: red; }                  /* tüm h1'ler */
.baslik { color: red; }             /* class="baslik" olanlar */
#ana-baslik { color: red; }         /* id="ana-baslik" olan tek element */
p.vurgulu { color: red; }           /* hem p hem class="vurgulu" */
div p { color: red; }               /* bir div İÇİNDEKİ tüm p'ler */
```

**`class` vs `id`:** `class` birden çok elemente uygulanabilir (tekrar kullanılabilir). `id` sayfada tek bir elemente ait olmalıdır (benzersiz) — bu ayrım JavaScript'te `getElementById` ile de karşına çıkar (bkz. [[07-dom-ve-events|DOM ve Events]]).

### Box Model

Her HTML elementi görünmez bir dikdörtgen kutudur, 4 katmanı vardır:

```
┌─────────────────────────────────────┐
│              margin                   │  (kutunun dışındaki boşluk)
│   ┌───────────────────────────────┐   │
│   │           border                │   │  (çerçeve)
│   │   ┌───────────────────────┐   │   │
│   │   │       padding            │   │   │  (içerik-çerçeve arası)
│   │   │   ┌───────────────┐   │   │   │
│   │   │   │    content      │   │   │   │  (asıl içerik)
│   │   │   └───────────────┘   │   │   │
│   │   └───────────────────────┘   │   │
│   └───────────────────────────────┘   │
└─────────────────────────────────────┘
```

```css
.kutu {
    padding: 10px;
    border: 2px solid black;
    margin: 20px;
}
```

`<div>` (block) vs `<span>` (inline) farkının kök sebebi `display` özelliğidir — bkz. [[01-html-nedir-temel-yapi|HTML Nedir?]].

## 3. Gerçek Dünya Bağlantısı

Backend developer CSS yazmasa da, bir hata raporunda ("yazı taşıyor", "buton büyük") bunun CSS mi yoksa backend'in gönderdiği hatalı/uzun veriden mi kaynaklandığını ayırt edebilmelidir. Örneğin çok uzun bir metin tasarımı bozuyorsa çözüm CSS değil, veri validasyonudur (Pydantic ile max karakter sınırı — AŞAMA 4'te işlenecek).

## Kritik Nokta

`margin`, kutunun **dışındaki** boşluktur (diğer elementlerle arası). `padding`, kutunun **içindeki** boşluktur (içerik ile çerçeve arası). Bir `<div>`'e `display: inline` verilerek `<span>` gibi davranması sağlanabilir — CSS, HTML'in varsayılan davranışlarını değiştirebilecek kadar esnektir.

## İlgili Notlar
- [[01-html-nedir-temel-yapi|HTML Nedir?]]
- [[05-css-flexbox-grid-responsive|Flexbox, Grid, Responsive]]
