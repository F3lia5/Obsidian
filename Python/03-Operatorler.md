#python #temel #operatorler

# Operatörler

## Amaç
Değişkenler ve değerler üzerinde işlem yapmayı sağlayan semboller — koşulların ve döngülerin temeli.

## Aritmetik Operatörler

| Operatör | Anlamı | Örnek |
|---|---|---|
| `+` | Toplama | `5 + 3` → `8` |
| `-` | Çıkarma | `5 - 3` → `2` |
| `*` | Çarpma | `5 * 3` → `15` |
| `/` | Bölme (ondalıklı) | `5 / 2` → `2.5` |
| `//` | Taban bölme (tam sayı) | `5 // 2` → `2` |
| `%` | Mod (kalan) | `5 % 2` → `1` |
| `**` | Üs alma | `5 ** 2` → `25` |

**Kritik:** `/` her zaman `float` döner, `//` "kaç tam sayı sığar" sorusuna cevap verir.

## Karşılaştırma Operatörleri

`==` (eşit mi), `!=` (eşit değil mi), `>`, `<`, `>=`, `<=`

**ÇOK ÖNEMLİ:** `=` atama yapar, `==` karşılaştırma yapar (`True`/`False` döner). Karıştırmak yaygın bir hatadır.

## Mantıksal Operatörler

`and` (her ikisi de doğru mu), `or` (en az biri doğru mu), `not` (tersini alır)

```python
if yas >= 18 and vize_var:
    print("Girebilirsin")
```

## Atama Operatörleri (Kısayollar)

```python
x = 5
x += 3   # x = x + 3
x -= 2
x *= 2
x /= 2
```

## Kimlik ve Üyelik Operatörleri (önizleme)
- `is` → iki değişken **aynı nesneye** mi işaret ediyor?
- `in` → bir eleman bir koleksiyonun içinde mi?

```python
>>> a = [1, 2, 3]
>>> 2 in a
True
```

## Görsel Mantık

```
   10 // 3 = 3   (10'un içine tam olarak 3 kere sığar)
   10 %  3 = 1   (3 kere sığdıktan sonra 1 kalır)

   Doğrulama: (10 // 3) * 3 + (10 % 3) = 10
```

Operatör önceliği:
```
2 + 3 * 4  → önce çarpma: 3*4=12 → 2+12=14   (2+3=5 sonra *4 DEĞİL!)
```

## Yaygın Hatalar
- `if x = 5:` → `=` ile `==` karıştırılmış → `SyntaxError`
- `5 / 2` sonucunun `2` olacağını sanmak → Python 3'te `/` her zaman float döner
- `and`/`or` yerine `&`/`|` kullanmak (bunlar bitwise operatörlerdir, farklı)
- Negatif sayılarda `//` ve `%` beklenmedik sonuç: `-7 // 2` → `-4` (Python "aşağı yuvarlama" yapar)

## Best Practice
- Karmaşık ifadelerde parantez kullan: `(a + b) * c`
- `x == True` yerine direkt `if x:` yaz (Pythonic)

## Kişisel Not — Artık Yıl Örneği
```python
sonuc = int(sayi) % 4
sonuc2 = int(sayi) % 100
sonuc3 = int(sayi) % 400
birlesim23 = sonuc2 != 0 or sonuc3 == 0
dogru = sonuc == 0 and birlesim23   # == True gereksiz, direkt boolean kullan
```
Kural: 4'e bölünebiliyor VE (100'e bölünemiyor YA DA 400'e bölünebiliyor) → artık yıl.

## Özet
- Aritmetik: `+ - * / // % **`. `/` float döner, `//` taban bölme yapar.
- Karşılaştırma: `== != > < >= <=` → `True`/`False` döner.
- `=` atama, `==` karşılaştırma — asla karıştırma.
- Mantıksal: `and`, `or`, `not`.
