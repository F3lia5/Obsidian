#python #veri-tipleri #listeler

# Listeler (Lists)

## Amaç
Birden fazla veriyi bir arada tutmak için Python'ın en temel veri yapısı.

## Tanımlama

```python
sayilar = [1, 2, 3, 4, 5]
isimler = ["Ali", "Veli", "Ayşe"]
karisik = [1, "iki", 3.0, True]   # farklı tipler bir arada olabilir
bos_liste = []
```

## Listeler **Mutable**'dır — String'in Tam Zıttı

```python
meyveler = ["elma", "armut"]
meyveler[0] = "muz"      # ÇALIŞIR (string'de TypeError verirdi)
```

## İndeksleme ve Dilimleme — String'le Aynı Mantık

```python
sayilar = [10, 20, 30, 40, 50]
sayilar[0]      # 10
sayilar[-1]     # 50
sayilar[1:3]    # [20, 30]
```

## Sık Kullanılan Metodlar

```python
liste = [3, 1, 4, 1, 5]

liste.append(9)        # sona eleman ekler
liste.insert(0, 100)     # belirli indekse ekler
liste.remove(1)           # DEĞERE göre ilk eşleşeni siler
liste.pop()                 # son elemanı siler VE döndürür
liste.pop(0)                  # belirtilen İNDEKSTEKİ elemanı siler VE döndürür
liste.sort()                    # sıralar (kalıcı)
liste.reverse()                  # ters çevirir (kalıcı)
len(liste)                          # eleman sayısı
sayi in liste                         # üyelik kontrolü
```

**Kritik fark:** `remove(deger)` değere göre siler, `pop(indeks)` konuma göre siler (ve değeri döndürür).

## Liste Kopyalama — Tehlikeli Tuzak

```python
a = [1, 2, 3]
b = a              # KOPYA DEĞİL, aynı listeye 2. bir etiket!
b.append(4)
print(a)           # [1, 2, 3, 4]  ← a da değişti!

# Gerçek kopya:
b = a.copy()     # ya da b = a[:]
b.append(4)
print(a)          # [1, 2, 3]  ← artık a etkilenmez
```

## Görsel Mantık

```
Bellek görünümü (b = a durumu):
  a ──┐
      ├──► [1, 2, 3, 4]   ← TEK liste nesnesi, iki etiket
  b ──┘

  a.copy() sonrası:
  a ──► [1, 2, 3]     (nesne 1)
  b ──► [1, 2, 3]     (nesne 2, bağımsız)
```

## Yaygın Hatalar
- `b = a` ile "kopyaladım" sanmak → aynı nesneye 2. etiket
- `liste.remove(deger)` ile indeks silmeye çalışmak → `remove()` değeri arar, indeks değil
- Boş listede `pop()` çağırmak → `IndexError`
- `liste = liste.append(x)` yazmak → `append()` `None` döner, listeyi kaybettirir!

## Best Practice
- Gerçek kopya için her zaman `.copy()` kullan
- `append()` sona ekler (hızlı), `insert()` konuma ekler (daha yavaş)

## Kişisel Not
`append()` gibi yerinde (in-place) değiştiren metodlar **`None` döndürür** çünkü zaten listeyi doğrudan değiştirmiştir, ayrıca yeni bir liste döndürmesine gerek yoktur:
```python
alisveris.append(urun)        # doğru
alisveris = alisveris.append(urun)   # YANLIŞ - alisveris artık None!
```

## Özet
- Listeler mutable — `append()`, `insert()`, `remove()`, `pop()` ile doğrudan değiştirilir.
- `b = a` kopya oluşturmaz, `.copy()` gerçek kopya oluşturur.
- Tekrar eden kod blokları (aynı döngünün birden fazla yerde yazılması) fonksiyonlarla çözülür.
