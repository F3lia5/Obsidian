#python #fonksiyonlar

# Fonksiyonlar (Functions)

## Amaç
Bir kod bloğunu isimlendirip istediğin kadar tekrar çağırabilmek — tekrar eden kodu (örn. iki kere yazılan bir for döngüsü) tek bir yerde toplamak.

## Temel Tanım ve Çağırma

```python
def selamla():
    print("Merhaba!")

selamla()   # ÇAĞIRMAK için parantez şart
```

**Kritik ayrım:** `def selamla():` fonksiyonu **tanımlar**, çalıştırmaz. `selamla()` **çağırır**, çalıştırır. (Tarif yazmak ≠ yemeği pişirmek)

## Parametre ve Argüman

```python
def selamla(isim):        # isim = PARAMETRE (tanımdaki yer tutucu)
    print(f"Merhaba, {isim}!")

selamla("Ahmet")            # "Ahmet" = ARGÜMAN (gerçek gönderilen değer)
```

## `return` — Sonucu Geri Vermek

```python
def topla(a, b):
    return a + b

sonuc = topla(3, 5)    # sonuc = 8
```

**`print` vs `return`:** `print()` sadece ekrana yazar, değeri dışarı taşımaz. `return`, değeri fonksiyonun dışına **taşır**.

```python
def yanlis_topla(a, b):
    print(a + b)        # sadece ekrana yazar

x = yanlis_topla(3, 5)   # ekrana 8 yazılır AMA
print(x)                  # None! fonksiyon hiçbir şey return etmedi
```

> Bu, `append()` konusundaki "yerinde işlem yapan fonksiyonlar None döner" mantığıyla aynı köke sahip bir tuzak.

## Varsayılan Parametre Değerleri

```python
def selamla(isim="Misafir"):
    print(f"Merhaba, {isim}!")

selamla()          # "Merhaba, Misafir!"
selamla("Ahmet")   # "Merhaba, Ahmet!"
```

## Scope'a Giriş (Detayı 12. derste)

Fonksiyon içinde tanımlanan değişkenler dışarıdan görünmez:
```python
def fonksiyon():
    x = 10

fonksiyon()
print(x)   # NameError!
```

## Görsel Mantık

```
def topla(a, b):        ← TANIM: "tarif yazıldı", henüz çalışmadı
    return a + b

topla(3, 5)              ← ÇAĞRI: "tarif uygulandı"
   │      │
   a=3   b=5
     │
     ▼
  return 3+5 = 8   ──► bu değer çağıranın yerine "geri döner"
```

## Yaygın Hatalar
- `return` yerine `print` kullanıp sonucu değişkende saklamaya çalışmak → `None` alırsın
- Fonksiyonu tanımlayıp çağırmayı unutmak (`selamla` ≠ `selamla()`)
- Fonksiyon içindeki değişkene dışarıdan erişmeye çalışmak → `NameError`

## Best Practice
- Fonksiyon isimleri fiil olmalı, ne yaptığını anlatmalı (`hesapla_kdv()`, `kullanici_dogrula()`)
- Bir fonksiyon tek bir iş yapmalı
- Değer üretip başka yerde kullanacaksan `return`, sadece ekrana yazdıracaksan `print`

## Özet
- `def` ile tanımlanır, `()` ile çağrılır.
- `return` değeri dışarı taşır; `print` sadece ekrana yazar.
- Varsayılan parametreler, argüman verilmediğinde devreye girer.
- Fonksiyon içi değişkenler dışarıdan görünmez (bkz. [[12-Scope]]).
