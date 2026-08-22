#python #list-comprehension #ileri-seviye

# List Comprehension

## Amaç
`for` döngüsü + `append()` kalıbını tek satıra indirmek — Pythonic kod yazmanın imzalarından biri.

## Temel Sözdizimi

```python
[ifade for eleman in iterable]
```

```python
# Klasik yol:
sonuc = []
for i in range(10):
    sonuc.append(i * 2)

# Comprehension hali (BİREBİR AYNI SONUÇ):
sonuc = [i * 2 for i in range(10)]
```

## Koşullu List Comprehension

```python
# sadece çift sayılar (filtreleme — if SONDA)
ciftler = [i for i in range(20) if i % 2 == 0]

# if/else ile (her eleman için değer üretme — if/else BAŞTA)
etiketler = ["çift" if i % 2 == 0 else "tek" for i in range(10)]
```

**Kritik fark:** Sadece `if` (filtreleme) → **sonda**. `if/else` (değer üretme) → **başta**, `for`'dan önce.

## String/Liste Üzerinde Kullanım

```python
kelime = "Python"
harfler = [h.upper() for h in kelime]   # ['P','Y','T','H','O','N']

sayilar = [1, 2, 3, 4, 5]
kareler = [x**2 for x in sayilar]        # [1, 4, 9, 16, 25]
```

## Dictionary Comprehension (bonus)

```python
kareler_dict = {x: x**2 for x in range(5)}
# {0:0, 1:1, 2:4, 3:9, 4:16}
```

## Görsel Mantık

```
   [ i*2   for i in range(5) ]
     ▲            ▲
     │            │
   üretilen    kaynak
    değer
```

## Yaygın Hatalar
- `if/else`'i sona yazmak → `SyntaxError`
- Çok karmaşık mantığı comprehension'a sıkıştırmak → okunabilirlik kaybı, klasik `for` tercih edilmeli
- Comprehension içinde yan etkili işlemler (`print()` gibi) yapmak → "Pythonic olmayan" kullanım

## Best Practice
- Basit dönüşüm/filtrelemede comprehension, karmaşık mantıkta klasik döngü

## Kişisel Not — İki Farklı Yaklaşım
```python
# Yöntem 1: if ile filtreleme (0-50 arası HER sayıyı üretip kontrol eder)
liste = [i for i in range(51) if i % 3 == 0]

# Yöntem 2: range'in step parametresiyle (direkt doğru sayıları üretir, kontrol yok)
liste = [i for i in range(0, 51, 3)]
```
İkisi de aynı sonucu verir. `step` yöntemi biraz daha **verimli** (gereksiz kontrol yapmaz), `if` yöntemi ise "3'e bölünenleri istiyorum" niyetini kodda daha **okunabilir** şekilde ifade eder.

## Özet
- `[ifade for eleman in iterable]` = klasik for+append'in kısa hali.
- Filtreleme (`if`) sonda, koşullu üretim (`if/else`) başta.
- Aşırı karmaşık mantığı sıkıştırma — okunabilirlik önceliklidir.
