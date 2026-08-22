#python #generator #ileri-seviye

# Generator

## Amaç
Elemanları tek tek, ihtiyaç oldukça üretmek — büyük veri setlerinde belleği verimli kullanmak. List comprehension her şeyi anında bellekte oluştururken, generator "tembel" (lazy) üretir.

## Generator Fonksiyonu — `yield`

Normal fonksiyon `return` ile bir kere değer döndürüp biter. Generator, `yield` ile değer üretir ve **fonksiyonun durumu korunur** — sonraki çağrıda kaldığı yerden devam eder.

```python
def sayac(limit):
    i = 0
    while i < limit:
        yield i
        i += 1

g = sayac(5)
print(next(g))   # 0
print(next(g))   # 1
print(next(g))   # 2
```

## `for` ile Kullanım (asıl pratik kullanım)

```python
for sayi in sayac(5):
    print(sayi)
# 0 1 2 3 4
```

## Generator Expression

`[ ]` yerine `( )` kullanılırsa generator expression olur:

```python
liste = [i**2 for i in range(1000000)]     # TÜM 1 milyon eleman ANINDA bellekte
gen = (i**2 for i in range(1000000))         # hiçbir şey henüz üretilmedi
```

## `return` vs `yield`

```python
def normal_fonksiyon():
    return [1, 2, 3]     # anında TÜM listeyi üretip döner, fonksiyon BİTER

def generator_fonksiyon():
    yield 1
    yield 2
    yield 3                # her yield'de DURUR, tekrar çağrılınca devam eder
```

## Görsel Mantık

```
Normal fonksiyon (return):          Generator (yield):
┌──────────────────┐                ┌──────────────────┐
│ TÜM sonucu hesapla│               │ yield 1 ──► DUR   │
│ TEK SEFERDE döndür│                │ (next() çağrılınca devam)
└──────────────────┘                │ yield 2 ──► DUR   │
      Bellek: hepsi anda             └──────────────────┘
                                       Bellek: sadece o an gereken
```

## Yaygın Hatalar
- Generator'ı direkt `print()` etmek → değerleri göstermez, `<generator object ...>` yazar. `for` ile tüketmek gerekir.
- Generator'ı ikinci kez kullanmaya çalışmak → generator **bir kere tüketilir**, listeyle farkı budur
- `[ ]` ile `( )` karıştırmak
- Generator'a indeksle erişmeye çalışmak (`gen[0]`) → `TypeError`

## Best Practice
- Çok büyük veri setlerinde generator kullan (bellek tasarrufu)
- Veriyi birden fazla kez kullanacaksan liste, bir kez sırayla işleyeceksen generator

## Kişisel Not — Sınır Kontrolü Generator'da da Geçerli
```python
def kareler(n):
    kare = 1                  # 1'den başlamak için (0 değil)
    while kare < n + 1:        # n dahil olsun diye (kare <= n ile aynı)
        yield kare**2
        kare += 1

for i in kareler(5):
    print(i)   # 1, 4, 9, 16, 25
```
"n dahil mi değil mi", "hangi değerden başlanmalı" soruları normal döngülerdeki gibi generator'da da dikkat gerektirir.

## Özet
- `yield` fonksiyonu generator'a çevirir — durur, `next()`/`for` ile devam eder.
- `( )` generator expression, `[ ]` normal liste; generator bellek açısından verimlidir.
- Generator'lar tek kullanımlıktır.
