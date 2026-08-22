#python #veri-tipleri #dictionary

# Dictionary

## Amaç
Veriyi anlamlı bir isimle (key) eşleştirerek tutmak — JSON, API cevapları hep bu mantıkla çalışır.

## Tanımlama — key:value Çiftleri

```python
kisi = {
    "isim": "Ahmet",
    "yas": 25,
    "sehir": "Ankara"
}
```

## Erişim

```python
kisi["isim"]        # "Ahmet"
kisi["meslek"]       # KeyError! Olmayan key'e direkt erişim riskli
kisi.get("meslek")    # None döner, hata vermez (güvenli erişim)
kisi.get("meslek", "Belirtilmemiş")   # key yoksa varsayılan değer
```

## Ekleme / Güncelleme / Silme

```python
kisi["meslek"] = "Mühendis"   # yeni key ekler (yoksa ekler, varsa günceller)
kisi["yas"] = 26                # var olanı günceller
del kisi["sehir"]                # siler
```

## Gezinme (Iteration)

```python
for key in kisi:
    print(key, kisi[key])

for key, value in kisi.items():   # daha Pythonic
    print(key, value)
```

## Key Kuralı — Immutable Olmalı

Key'ler string, int, tuple olabilir; **liste olamaz** (mutable olduğu için).

```python
d = {(1,2): "koordinat"}   # ✅ çalışır, tuple immutable
d = {[1,2]: "koordinat"}   # ❌ TypeError, liste mutable
```

## Görsel Mantık

```
kisi = {"isim": "Ahmet", "yas": 25}

   key ──────► value
  "isim" ────► "Ahmet"

Liste ile fark:
  Liste:  [0]────►"Ahmet"   (key = sabit indeks numarası)
  Dict:   ["isim"]──►"Ahmet" (key = anlamlı isim)
```

## Yaygın Hatalar
- `kisi["olmayan_key"]` ile direkt erişmek → `KeyError`
- Listeyi key olarak kullanmaya çalışmak → `TypeError`
- `.items()` kullanmadan `for key, value in kisi:` yazmak → hata

## Best Practice
- Key'in var olup olmadığından emin değilsen `.get()` kullan
- Key-value ikisine de ihtiyaç varsa `.items()` ile gez

## Kişisel Not — `.get()`'in Gerçek Gücü
Her key için ayrı `if/elif` yazmak yerine:
```python
# Gereksiz uzun:
if search == "apple": print(stock.get("apple"))
elif search == "peach": print(stock.get("peach"))
...

# Doğru kullanım — tek satırda dinamik sorgu:
miktar = stock.get(search)
if miktar is not None:
    print(f"{miktar} {search} stokta var")
else:
    print("Bu ürün stokta yok")
```
`.get()`'in asıl amacı, her key için ayrı kontrol yazma ihtiyacını ortadan kaldırmaktır.

## Özet
- Dictionary key-value çiftleriyle veri tutar.
- `d[key]` riskli (`KeyError`), `.get()` güvenli (`None` ya da varsayılan döner).
- Key'ler immutable olmalı (string, int, tuple olur; liste olmaz).
