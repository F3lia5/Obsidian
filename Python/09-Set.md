#python #veri-tipleri #set

# Set

## Amaç
Listeye benzer ama **sırasız** ve **tekrar eleman içermez** — tekrar temizleme ve küme işlemleri için ideal.

## Tanımlama

```python
renkler = {"kırmızı", "yeşil", "mavi"}
bos_set = set()   # DİKKAT: {} boş DICTIONARY demektir, boş set için set() gerekir!
```

## Otomatik Tekrar Temizleme

```python
sayilar = {1, 2, 2, 3, 3, 3}
print(sayilar)   # {1, 2, 3}
```

Bir listeyi hızlıca tekrarsız hale getirmek için: `list(set(liste))`

## Sırasızlık — İndeksleme Yok

```python
renkler[0]   # TypeError! Set indekslenemez
```

## Küme İşlemleri

```python
a = {1, 2, 3}
b = {2, 3, 4}

a | b   # birleşim (union)     → {1, 2, 3, 4}
a & b   # kesişim (intersection) → {2, 3}
a - b   # fark (difference)     → {1}
```

## Metodlar

```python
s = {1, 2, 3}
s.add(4)         # eleman ekler
s.remove(2)      # eleman siler (yoksa KeyError!)
s.discard(99)    # eleman siler (yoksa hata VERMEZ, sessizce geçer)
```

## Görsel Mantık

```
a = {1, 2, 3}        b = {2, 3, 4}

   a          a & b         b
 ┌───┐      ┌─────┐      ┌───┐
 │ 1 │      │ 2,3 │      │ 4 │
 └───┘      └─────┘      └───┘
   └── a | b = {1,2,3,4} ──┘
        a - b = {1}  (sadece a'da olan)
```

## Yaygın Hatalar
- `bos = {}` yazıp bunu boş set sanmak → `{}` boş dictionary'dir
- Set'e indeksle erişmeye çalışmak → `TypeError`
- `remove()` ile olmayan elemanı silmeye çalışmak → `KeyError`

## Best Practice
- Tekrarları temizlemek için `list(set(liste))`
- "Ortak eleman" gibi sorularda küme işlemlerini (`&`, `|`, `-`) kullan, döngüyle uğraşma

## Özet
- Set: sırasız, tekrarsız, indekslenemez.
- `{}` dictionary, boş set için `set()`.
- `|` birleşim, `&` kesişim, `-` fark.
- `remove()` hata riski taşır, `discard()` güvenli silme sağlar.
