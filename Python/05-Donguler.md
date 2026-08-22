#python #temel #donguler

# Döngüler (for, while)

## Amaç
Tekrar gerektiren işlemleri otomatikleştirmek.

## `for` Döngüsü
Bir dizi/koleksiyon üzerinde (veya belirli sayıda) gezinmek için.

```python
for sayi in range(5):
    print(sayi)   # 0,1,2,3,4
```

`range()` kullanımları:
```python
range(5)        # 0,1,2,3,4       (0'dan başlar, 5 HARİÇ)
range(2, 5)     # 2,3,4           (2'den başlar, 5 hariç)
range(0, 10, 2) # 0,2,4,6,8       (2'şer atlar)
```

String/liste üzerinde de gezinilebilir:
```python
for harf in "Python":
    print(harf)
```

## `while` Döngüsü
Bir koşul True olduğu sürece tekrar eder — kaç kere döneceğini bilmiyorsan tercih edilir.

```python
sayac = 0
while sayac < 5:
    print(sayac)
    sayac += 1   # KRİTİK: unutulursa sonsuz döngü!
```

## `break` ve `continue`
- `break` → döngüyü tamamen sonlandırır
- `continue` → mevcut adımı atlar, sonraki tekrara geçer

```python
for sayi in range(10):
    if sayi == 5:
        break        # 0 1 2 3 4
    print(sayi)

for sayi in range(10):
    if sayi % 2 == 0:
        continue     # 1 3 5 7 9
    print(sayi)
```

## Döngülerde `else` (az bilinen özellik)
Döngü `break` ile kesilmeden normal biterse çalışır.

```python
for sayi in range(5):
    if sayi == 10:
        break
else:
    print("Döngü break olmadan tamamlandı")   # bu çalışır
```

## Görsel Mantık

```
while kosul:
   ┌──────────────┐
   │ kosul True mu?│──No──► döngüden çık
   └───────┬───────┘
          Yes
           │
      kod çalışır
           │
           └──────► başa dön, tekrar kontrol et
```

## Yaygın Hatalar
- `while` içinde sayaç güncellemeyi unutmak → sonsuz döngü
- `range(5)` sonucunun 1-5 olacağını sanmak → aslında 0-4
- `break`/`continue` karıştırmak
- Döngü sırasında üzerinde gezinilen listeyi değiştirmek (ileri konu, beklenmedik davranış)

## Best Practice
- Kaç kere döneceğini biliyorsan `for`, bilmiyorsan/koşula bağlıysa `while`
- `while True:` + `break` kalıbı, "koşul sağlanana kadar dene" senaryolarında çok kullanışlı

## Kişisel Not — Toplama Kalıbı
```python
toplam = 0   # döngü DIŞINDA başlatılmalı, yoksa her turda sıfırlanır

while True:
    sayi = int(input("Sayı girin (çıkmak için -1): "))
    if sayi == -1:
        break
    toplam += sayi

print("Toplam:", toplam)
```
Döngü dışında tanımlanan değişken, döngü boyunca değerini korur — biriktirme/toplama mantığının temeli budur.

## Özet
- `for`: bilinen sayıda/koleksiyon üzerinde tekrar. `while`: koşula bağlı tekrar.
- `range(start, stop, step)` — `stop` her zaman hariç.
- `break` döngüyü bitirir, `continue` adımı atlar.
