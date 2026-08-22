#python #standart-kutuphane

# Standart Kütüphaneler

## Amaç
Python'ın "pilleri dahil" (batteries included) felsefesi — kurulum gerektirmeden hazır gelen, gerçek projelerde sık kullanılan kütüphaneler.

## `datetime` — Tarih ve Saat

```python
import datetime

simdi = datetime.datetime.now()
print(simdi.year, simdi.month, simdi.day)
print(simdi.strftime("%Y-%m-%d %H:%M"))   # okunabilir format

dogum_tarihi = datetime.date(2000, 5, 15)
yas_hesabi = datetime.date.today() - dogum_tarihi
print(yas_hesabi.days)
```

> `datetime.datetime.now()` — modülün adı da, sınıfın adı da `datetime`, bu yüzden çift yazılır.

## `os` — İşletim Sistemi ile Etkileşim

```python
import os

print(os.getcwd())                    # çalışma dizini
print(os.listdir("."))                 # klasördeki dosyalar
print(os.path.exists("dosya.txt"))     # dosya var mı
print(os.path.join(dizin, dosya_adi))   # platform bağımsız yol birleştirme
```

## `json` — Veri Değişim Formatı (API'lerde çok kullanılır)

```python
import json

kisi = {"isim": "Ali", "yas": 25}

json_string = json.dumps(kisi)     # dict → JSON string
geri = json.loads(json_string)       # JSON string → dict

with open("veri.json", "w") as f:
    json.dump(kisi, f)                 # dict → doğrudan dosyaya

with open("veri.json", "r") as f:
    veri = json.load(f)                 # dosya → dict
```

**Fark:** `dumps`/`loads` (s ile) → string ile çalışır. `dump`/`load` (s'siz) → doğrudan dosyayla çalışır.

**Türkçe karakter sorunu:** `json.dumps(veri, ensure_ascii=False)` kullanılmazsa Türkçe karakterler `\u00e7` gibi kod dizilerine döner.

## `collections.Counter` — Sayım/İstatistik

```python
from collections import Counter

kelimeler = ["elma", "armut", "elma", "muz", "elma"]
sayac = Counter(kelimeler)
print(sayac)                    # Counter({'elma': 3, 'armut': 1, 'muz': 1})
print(sayac.most_common(1))      # [('elma', 3)]
```

## `re` — Regular Expressions (kısa önizleme)

```python
import re

metin = "İletişim: ahmet@gmail.com"
sonuc = re.search(r"[\w.]+@[\w.]+", metin)
print(sonuc.group())    # "ahmet@gmail.com"
```

## Yaygın Hatalar
- `json.dumps` ile `json.dump` karıştırmak
- `datetime.now()` yazıp `datetime.datetime.now()` demeyi unutmak
- JSON'da Türkçe karakterlerin bozuk çıkması (`ensure_ascii=False` unutulursa)

## Özet
- `datetime` → tarih/saat, `os` → dosya sistemi.
- `json.dumps/loads` string ile, `json.dump/load` dosya ile çalışır.
- `Counter` → eleman sayımını tek satırda yapar.
- `re` → metin içinde kalıp arama (ileri seviye konu, ayrıca öğrenilmeli).
