#python #veri-tipleri #tuple

# Tuple

## Amaç
Listeye benzer ama **immutable** (değiştirilemez) sıralı veri yapısı. "Ne zaman liste, ne zaman tuple?" sorusuna cevap.

## Tanımlama

```python
koordinat = (10, 20)
renkler = ("kırmızı", "yeşil", "mavi")
tek_elemanli = (5,)     # DİKKAT: virgül şart! (5) tuple DEĞİL, sadece int 5
bos_tuple = ()
```

**Kritik detay:** Tuple'ı asıl tanımlayan **virgüldür**, parantez opsiyoneldir:
```python
x = 1, 2, 3    # geçerli bir tuple
```

## Immutable — String'le Aynı Mantık

```python
koordinat = (10, 20)
koordinat[0] = 99    # TypeError!
```

## Neden Tuple Kullanılır?

1. **Anlam/niyet belirtme:** "Bu veri değişmeyecek" mesajı verir (koordinat, tarih gibi)
2. **Güvenlik:** Fonksiyona gönderildiğinde yanlışlıkla değiştirilemez
3. **Performans:** Listeye göre daha az bellek, biraz daha hızlı
4. **Dictionary key olarak kullanılabilir** (liste kullanılamaz, çünkü mutable)

> Mantık zinciri: önce "bu veri değişmemeli" kararı verilir, **sonra** tuple seçilir — sebep tuple'ın immutable olması değil, verinin değişmemesi gerektiğidir.

## Unpacking (Ayrıştırma)

```python
koordinat = (10, 20)
x, y = koordinat     # x=10, y=20

# split() ile de aynı mantık kullanılmıştı:
username, domain = "ali@gmail.com".split("@", 1)
```

## İndeksleme/Slicing — Aynı Mantık

```python
renkler = ("kırmızı", "yeşil", "mavi")
renkler[0]      # "kırmızı"
renkler[1:3]    # ("yeşil", "mavi")
```

## Görsel Mantık

```
Unpacking:
   kisi = ("Ahmet", 25, "Mühendis")
              │      │        │
              ▼      ▼        ▼
             ad     yas    meslek
```

## Yaygın Hatalar
- `tek_elemanli = (5)` yazıp tuple sanmak → virgül olmadan bu sadece bir `int`
- Tuple'ı değiştirmeye çalışmak → `TypeError`
- Unpacking'de eleman sayısı uyuşmazlığı → `x, y = (1, 2, 3)` → `ValueError`

## Best Practice
- Veri değişmeyecekse (sabit koordinat, RGB, tarih) tuple kullan
- Veri değişecek/büyüyecekse liste kullan

## Kişisel Not — for Döngüsünde Unpacking
```python
ogrenciler = [("Zeynep", 16, "10-A"), ("Ali", 17, "11-B")]
for ad, yas, sinif in ogrenciler:
    print(f"{ad} {yas} {sinif}")
```
Unpacking, tekli bir tuple'da olduğu gibi `for` döngüsü içinde de çalışır — her tuple otomatik olarak parçalarına ayrılır.

## Özet
- Tuple = sıralı, immutable veri yapısı.
- Virgül tuple'ı tanımlar, parantez opsiyonel; tek elemanlı tuple `(x,)` olmalı.
- Unpacking hem tekli hem döngü içinde çalışır.
- Değişmemesi gereken veri için tuple, değişecek veri için liste.
