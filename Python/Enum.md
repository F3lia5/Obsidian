#python #enum #oop

# Enum

> Bu not [[20-Ileri-Python]] dersinin bir alt konusudur.

## Amaç
Bir değişkenin **sadece belirli, sabit değerlerden** birini alabileceği durumlarda kullanılır (örneğin bir siparişin durumu: beklemede/tamamlandı/iptal). String yazım hatalarını (`"beklemde"` gibi typo'ları) önler.

## Tanımlama

```python
from enum import Enum

class SiparisDurumu(Enum):
    BEKLEMEDE = 1
    TAMAMLANDI = 2
    IPTAL = 3
```

## Kullanım

```python
durum = SiparisDurumu.BEKLEMEDE

print(durum)          # SiparisDurumu.BEKLEMEDE
print(durum.name)     # "BEKLEMEDE"
print(durum.value)    # 1
```

## Neden String Yerine Enum?

```python
# String ile — RİSKLİ
durum = "beklemede"
if durum == "beklemde":   # typo! sessizce False döner, hata vermez
    ...

# Enum ile — GÜVENLİ
durum = SiparisDurumu.BEKLEMEDE
if durum == SiparisDurumu.BEKELMEDE:   # typo! AttributeError, hata HEMEN yakalanır
    ...
```

String'de typo, programı **sessizce yanlış çalıştırır** (en tehlikeli hata türü — fark etmek zor). Enum'da typo, Python tarafından **hemen** yakalanır.

## Görsel Mantık

```
class SiparisDurumu(Enum):
    BEKLEMEDE = 1   ┐
    TAMAMLANDI = 2   ├─ sabit, değişmez üyeler
    IPTAL = 3        ┘

SiparisDurumu.BEKLEMEDE
        │        │
      sınıf    üye (name: "BEKLEMEDE", value: 1)
```

## Karşılaştırma

```python
d1 = SiparisDurumu.BEKLEMEDE
d2 = SiparisDurumu.BEKLEMEDE
print(d1 == d2)                        # True (aynı üye)
print(d1 == SiparisDurumu.IPTAL)       # False
```

## Yaygın Hatalar
- Enum değerlerini string gibi karşılaştırmaya çalışmak (`durum == "BEKLEMEDE"`) → çalışmaz, `durum == SiparisDurumu.BEKLEMEDE` şeklinde karşılaştırılmalı
- `.value` ile `.name` karıştırmak — `.name` string isim (`"BEKLEMEDE"`), `.value` atanan değer (`1`)

## Ne Zaman Kullanılır?
- Sabit, sınırlı seçenek kümeleri: durum (status), kategori, tip, rol gibi alanlarda
- Bir dictionary'de "geçerli anahtarlar" listesi yerine

## Bağlantılı Notlar
- [[20-Ileri-Python]] — dataclass, magic methods, iterator ile birlikte ele alınmıştı
- [[19-OOP]] — Enum da aslında özel bir sınıf türüdür (Enum'dan miras alır)
- [[04-Kosullar]] — `==` karşılaştırması burada da geçerli

## Özet
- `Enum`, sabit seçenek kümelerini string yazım hatalarına karşı güvenli hale getirir.
- `.name` → isim, `.value` → atanan değer.
- Typo'lar Enum'da hemen (`AttributeError`) yakalanır, string'de sessizce geçebilir.
