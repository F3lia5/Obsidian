#python #oop #ileri-seviye

# Object Oriented Programming (OOP)

## Amaç
İlişkili veri ve davranışı **tek bir yapı (sınıf/class)** altında birleştirmek. GitHub'daki ciddi projelerin (Django, Flask, oyunlar, API'ler) temel iskeleti.

## Sınıf (Class) ve Nesne (Object/Instance)

**Sınıf** = şablon/kalıp. **Nesne** = o şablondan üretilmiş gerçek bir örnek.

> Benzetme: "Araba" bir sınıftır (genel tanım). Garajdaki kırmızı Toyota bir nesnedir (somut örnek).

```python
class Araba:
    pass

araba1 = Araba()   # bir NESNE oluşturduk
```

## `__init__` — Kurucu Metod

Nesne oluşturulduğunda otomatik çalışır, başlangıç değerlerini ayarlar.

```python
class Araba:
    def __init__(self, marka, renk):
        self.marka = marka
        self.renk = renk

araba1 = Araba("Toyota", "kırmızı")
print(araba1.marka)   # "Toyota"
```

**`self`** = "bu metodun çalıştığı o anki nesnenin kendisi". İlk parametre olarak otomatik gelir, Python kendisi doldurur.

## Metod

```python
class Araba:
    def __init__(self, marka, renk):
        self.marka = marka
        self.renk = renk

    def bilgi_ver(self):
        print(f"Bu araba {self.renk} renkli bir {self.marka}")

araba1.bilgi_ver()
```

## Attribute (Öznitelik)

`self.marka`, `self.renk` → her nesnenin kendine özel bir kopyası vardır.

## Class Attribute vs Instance Attribute

```python
class Araba:
    tekerlek_sayisi = 4    # CLASS attribute — TÜM nesneler arasında ORTAK

    def __init__(self, marka):
        self.marka = marka   # INSTANCE attribute — her nesneye ÖZEL
```

## Inheritance (Kalıtım) — Önizleme

```python
class Arac:
    def __init__(self, marka):
        self.marka = marka

class Araba(Arac):    # Araba, Arac'tan MİRAS alıyor
    pass
```

## Yaygın Hatalar
- `self` parametresini unutmak → `TypeError`
- `self.marka` yerine sadece `marka` yazmak → değer nesneye kalıcı kaydedilmez (local scope'ta kalır)
- Sınıf tanımı (`Araba`) ile nesne oluşturma (`Araba()`) karışıklığı

## İsimlendirme Kuralları (PEP 8)
- **Sınıf isimleri**: PascalCase (`Ogrenci`, `KullaniciHesabi`)
- **Metod isimleri**: snake_case (`ortalama_hesapla`, fonksiyonlarla aynı kural)

## Kişisel Not
`class ogrenci` yerine `class Ogrenci`, `OrtalamaHesapla` yerine `ortalama_hesapla` olmalı — sınıf/metod isimlendirme kuralları birbirinin tam tersi stilde.

## Özet
- Sınıf = şablon, nesne = somut örnek.
- `__init__` otomatik çalışan kurucu, `self` = o anki nesne.
- `self.x` ile tanımlanan attribute'lar nesneye kalıcı bağlanır.
- Aynı sınıftan üretilen nesneler birbirinden bağımsızdır.
