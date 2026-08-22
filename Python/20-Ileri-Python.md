#python #oop #ileri-seviye

# İleri Python (Iterator, Magic Methods, Dataclass, Enum)

## Amaç
OOP bilgisini profesyonel Python seviyesine taşıyan 4 konu.

## Magic Methods (Dunder Methods)

`__init__` gibi çift alt çizgili metodlar, sınıfının Python'ın yerleşik davranışlarıyla (print, toplama, karşılaştırma) entegre olmasını sağlar.

```python
class Ogrenci:
    def __init__(self, isim, notlar):
        self.isim = isim
        self.notlar = notlar

    def __str__(self):
        # print(nesne) çağrıldığında NE gösterileceğini belirler
        return f"Öğrenci: {self.isim}"

    def __eq__(self, other):
        # nesne1 == nesne2 karşılaştırmasında NE kontrol edileceğini belirler
        return self.isim == other.isim
```

`__str__` olmadan `print(nesne)` → `<__main__.Ogrenci object at 0x...>` gibi anlamsız bir çıktı verir.

## Iterator — `for` Döngüsünün Perde Arkası

`__iter__` ve `__next__` metodlarıyla kendi iterasyon mantığını kurabilirsin.

```python
class Sayac:
    def __init__(self, limit):
        self.limit = limit
        self.sayi = 0

    def __iter__(self):
        return self

    def __next__(self):
        if self.sayi >= self.limit:
            raise StopIteration
        self.sayi += 1
        return self.sayi

for i in Sayac(3):
    print(i)   # 1 2 3
```

> `yield` (Generator dersi) aslında bunu arka planda otomatik yapıyordu — bu, manuel/sınıf tabanlı hali.

## `dataclass` — Basit Veri Sınıfları İçin Kısayol

```python
from dataclasses import dataclass

@dataclass
class Ogrenci:
    isim: str      # DİKKAT: ':' kullanılır, '=' DEĞİL
    yas: int

o1 = Ogrenci("Ali", 20)
print(o1)    # Ogrenci(isim='Ali', yas=20)  ← otomatik __init__ ve __repr__
```

`@dataclass`, `__init__` ve `__repr__`'i otomatik üretir. Kendi metodlarını eklemeye devam edebilirsin, `self` kullanımı normal sınıflarla birebir aynı:

```python
@dataclass
class Kitap:
    baslik: str
    sayfa: int

    def bilgi_ver(self):
        return f"{self.baslik} kitabi {self.sayfa} sayfadan olusuyor"
```

## `Enum` — Sabit Seçenek Kümeleri

```python
from enum import Enum

class SiparisDurumu(Enum):
    BEKLEMEDE = 1
    TAMAMLANDI = 2
    IPTAL = 3

durum = SiparisDurumu.BEKLEMEDE
print(durum.name)     # "BEKLEMEDE"
print(durum.value)    # 1
```

**Neden string yerine Enum?** String'de typo (`"beklemde"`) sessizce geçer. Enum'da typo `AttributeError` verir — hata erken yakalanır.

## Yaygın Hatalar
- `__next__` içinde `StopIteration` fırlatmayı unutmak → sonsuz döngü
- `dataclass`'ta tip belirtimini (`: str`) atlayıp `=` kullanmak → alan doğru tanınmaz
- Enum değerlerini string gibi karşılaştırmaya çalışmak

## Kişisel Not
`baslik = str` ile `baslik: str` çok farklı — ilki `baslik` değişkenine `str` tipinin kendisini atar (yanlış), ikincisi tip belirtimidir (`dataclass`'ın beklediği doğru sözdizimi).

## Özet
- Magic method'lar → print/karşılaştırma gibi yerleşik davranışları özelleştirir.
- Iterator protokolü → `for` döngüsünün perde arkası, generator'ın manuel hali.
- `dataclass` → tekrar eden `__init__`/`__repr__` yazımını otomatikleştirir.
- `Enum` → sabit seçenek kümelerini güvenli hale getirir.
