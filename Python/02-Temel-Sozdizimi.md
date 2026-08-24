#python #temel #sozdizimi

# Temel Sözdizimi

## Amaç
Python'ın dilbilgisi kurallarını öğrenmek — bloklar, yorumlar, değişkenler, isimlendirme.

## Girinti (Indentation)
Python bloklarını `{ }` yerine **girinti (4 boşluk)** ile belirler — bu zorunlu bir kuraldır, stil tercihi değil.

```python
if True:
    print("if bloğuna ait")
print("if bloğunun dışında")
```

PEP 8: her zaman **4 boşluk**, tab kullanma.

## Yorum Satırları

```python
# tek satırlık yorum
```

Çok satırlı yorum için genelde üçlü tırnak (`"""..."""`) kullanılır (aslında docstring'dir, teknik olarak yorum değildir).

## Değişkenler ve Atama

```python
isim = "Ahmet"
yas = 25
```

Python **dinamik tipli**dir — tip belirtmene gerek yok, Python değere bakarak kendisi belirler (ama tipsiz değildir, her değerin bir tipi vardır).

## Değişken İsimlendirme Kuralları (PEP 8)
- Harf, rakam, alt çizgi kullanılabilir, **rakamla başlayamaz**
- **case-sensitive**: `isim` ≠ `Isim`
- **snake_case** kullanılmalı: `kullanici_adi` (camelCase Python'da yaygın değil)
- Anlamlı isimler kullan: `x` yerine `yas`

## Satır Sonu
Python'da `;` gerekmez (koyulabilir ama PEP 8 önermez).

## Görsel Mantık

```
if yas >= 18:
│   print("Reşitsin")     ← 4 boşluk girintili → if bloğuna ait
│   print("Oy kullanabilirsin")  ← aynı blok
print("Program bitti")    ← girinti yok → if bloğunun DIŞINDA
```

## Yaygın Hatalar
- `IndentationError` → aynı blok içinde tutarsız girinti
- `2isim = "Ali"` → rakamla başlayan değişken adı → `SyntaxError`
- `isim = Ahmet` (tırnaksız) → Python bunu bir değişken adı sanır → `NameError`
- `kullaniciAdi` gibi camelCase kullanmak → PEP 8 ihlali
- Tab ve boşluğu karıştırmak → `TabError`

## Best Practice
- Editörde tab tuşuna basınca otomatik 4 boşluk girmesini sağla (nvim: `:set expandtab shiftwidth=4 tabstop=4`)
- Sabit değerler için `BÜYÜK_HARF_SNAKE_CASE` kullanılır (örn. `MAX_DENEME_SAYISI = 3`)

## Kişisel Not — Değişkenler Aslında "Kutu" Değil, "Etiket"tir
```python
isim = "Ahmet"   # isim, bir string nesnesine işaret eden bir ETİKET
isim = 25          # isim artık YENİ bir int nesnesine işaret ediyor
```
C gibi statik tipli dillerde değişken sabit boyutlu bir "kutu"dur (sadece belirlenen tipi tutar). Python'da değişken bir **referans/etiket**tir — hangi nesneye işaret ettiğini değiştirebilir, bu yüzden dinamik tipleme mümkündür. Eski nesne, kimse işaret etmediğinde çöp toplayıcı (garbage collector) tarafından temizlenir.

## Özet
- Bloklar girinti (4 boşluk) ile belirlenir, `{ }` yok.
- Değişkenler `isim = değer`, tip belirtmeye gerek yok.
- Değişken isimleri rakamla başlayamaz, snake_case kullanılmalı.
- `type()` fonksiyonu bir değerin tipini gösterir.
