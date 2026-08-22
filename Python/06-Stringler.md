#python #veri-tipleri #stringler

# Stringler (Strings)

## Amaç
Metin verileriyle çalışmak — kullanıcı adları, mesajlar, dosya yolları vs.

## Tanımlama

```python
isim = "Ahmet"
soyisim = 'Yılmaz'      # tek ya da çift tırnak fark etmez
cumle = """Bu
çok satırlı
bir string"""
```

## Stringler **Immutable**'dır (Değiştirilemez)

```python
isim[0] = "M"   # TypeError! 
```

Bir stringi "değiştirmek" istediğinde Python aslında **yeni bir string oluşturur**, eskisi değişmez.

## İndeksleme ve Dilimleme (Slicing)

```python
kelime = "Python"
#          P  y  t  h  o  n
#          0  1  2  3  4  5
#         -6 -5 -4 -3 -2 -1

kelime[0]     # 'P'
kelime[-1]    # 'n'  (son karakter)
kelime[1:4]   # 'yth'  (1'den başlar, 4 HARİÇ)
kelime[:3]    # 'Pyt'
kelime[3:]    # 'hon'
kelime[::-1]  # 'nohtyP'  (tersten yazdırma)
```

## Sık Kullanılan Metodlar

```python
s = "  Merhaba Dünya  "

s.upper()             # büyütür
s.lower()              # küçültür
s.strip()               # baştaki/sondaki boşlukları siler
s.replace("a", "e")      # karakter değiştirir
s.split(" ")              # boşluğa göre parçalayıp liste yapar
len(s)                      # uzunluk
s.find("Dünya")               # bulduğu indeksi döner, bulamazsa -1
```

## `split()` Parametreleri

```python
lower_mail.split("@", 1)
```
- `sep` → ayraç karakteri
- `maxsplit` → kaç kere bölüneceği

```python
"a@b@c".split("@")     # ['a', 'b', 'c']  → hepsinden böler
"a@b@c".split("@", 1)  # ['a', 'b@c']     → sadece İLK @'de böl (2 parça garanti)
"a@b@c".rsplit("@", 1) # ['a@b', 'c']     → SONdan böl
```

`maxsplit=1`, birden fazla değişkene atama (`x, y = ...`) yaparken **tam parça sayısı garantisi** sağlar (`ValueError` riskini önler).

## String Birleştirme ve f-string

```python
ad = "Ali"
yas = 25

mesaj = "Adım " + ad + ", yaşım " + str(yas)   # eski yöntem, int'i str()'e çevirmen gerekir
mesaj = f"Adım {ad}, yaşım {yas}"                # modern, tercih edilen yöntem
```

## Yaygın Hatalar
- `isim[0] = "M"` → `TypeError` (immutable)
- `"yaşım " + 25` → `str` ile `int`'i `+` ile birleştirememe → `TypeError`
- `kelime[6]` (6 harfli kelimede) → `IndexError`
- Slicing'de "stop dahil" sanmak → dahil değildir

## Best Practice
- Birleştirmede f-string tercih et
- Kullanıcı input'larında `strip()` kullanmayı alışkanlık haline getir
- Karşılaştırmada `lower()`/`upper()` ile normalize et

## Kişisel Not
`strip()` gibi metodlar orijinal string'i **değiştirmez**, yeni bir string **döndürür** — dönen değeri bir değişkene atamazsan (ya da yanlış değişkeni kullanırsan) kaybolur:
```python
mail = raw_mail.strip()        # doğru
lower_mail = raw_mail.lower()   # YANLIŞ - strip sonucu kullanılmadı!
lower_mail = mail.lower()        # doğru
```

## Özet
- Stringler immutable — metodlar yeni string döndürür, orijinali değiştirmez.
- İndeksleme 0'dan başlar, slicing'de stop dahil değil.
- `split(sep, maxsplit)` ile kontrollü bölme yapılabilir.
