#python #hata-yonetimi

# Hata Yönetimi (Exception Handling)

## Amaç
Kullanıcının her zaman doğru veri gireceğini varsayamayız — programın çökmesini önleyip düzgün bir mesaj göstermek.

## Exception Nedir?
`TypeError`, `ValueError`, `KeyError`, `IndexError`, `NameError` gibi hatalar birer **exception**'dır. Önlem alınmazsa program çöker.

## `try` / `except`

```python
try:
    sayi = int(input("Bir sayı girin: "))
    print(100 / sayi)
except ValueError:
    print("Geçerli bir sayı girmediniz!")
except ZeroDivisionError:
    print("Sıfıra bölemezsin!")
```

Hata oluşursa Python **hemen** `except` bloğuna atlar (try içindeki kalan satırlar atlanır).

## Birden Fazla Hata Türü

```python
except (ValueError, ZeroDivisionError):
    print("Bir hata oluştu")

except Exception as e:
    print(f"Beklenmeyen bir hata: {e}")
```

**Uyarı:** `except:` (bare, tür belirtmeden) PEP 8'e aykırıdır — her şeyi susturur, debug'ı zorlaştırır. Her zaman **spesifik** hata türü yakala.

## `else` ve `finally`

```python
try:
    sayi = int(input("Sayı: "))
except ValueError:
    print("Hatalı giriş")
else:
    print(f"Girdiğiniz sayı: {sayi}")   # sadece hata OLMAZSA çalışır
finally:
    print("İşlem tamamlandı")            # hata olsun olmasın HER ZAMAN çalışır
```

`else` bloğu, "hata varsa dur, yoksa devam et" mantığını temiz kurmak için kullanılır — `except`'ten sonraki kodu doğrudan `else` içine koymak, hatalı girdiden sonra istenmeyen kodun çalışmasını engeller.

## `raise` — Kendi Hatanı Fırlatmak

```python
yas = -5
if yas < 0:
    raise ValueError("Yaş negatif olamaz!")
```

## Görsel Mantık

```
try:
   ┌─────────────────────┐
   │ riskli_kod()         │
   │                      │  hata olursa ──► except bloğuna ATLA
   └─────────────────────┘
             │
        hata yoksa
             ▼
        else bloğu (varsa)
             │
             ▼
        finally bloğu (HER ZAMAN çalışır)
```

## Yaygın Hatalar
- `except:` (tür belirtmeden) kullanmak → her hatayı sessizce yutar
- `try` bloğuna gereğinden fazla kod koymak → hangi satırın hata verdiği belirsizleşir
- Hatayı yakalayıp hiçbir şey yapmamak (`pass`) → sorun sessizce yutulur

## Best Practice
- Sadece gerçekten olabilecek hataları, spesifik olarak yakala
- `try` bloğunu mümkün olduğunca dar tut
- Kullanıcıya anlaşılır bir mesaj göster

## Kişisel Not — Menü Sistemi Örneği
```python
try:
    secim = int(input("Seçiminiz: "))
except ValueError:
    print("Lütfen sadece sayı girin")
else:
    if secim == 1:
        ...
    elif secim == 2:
        ...
```
`else` bloğunun içine `if/elif` zincirini koymak, "hatalı giriş" mesajıyla "geçerli seçenek" mesajının **aynı anda** çıkmasını (mantıksal karışıklığı) önler — çünkü `int()` başarısız olursa `else` bloğuna hiç girilmez.

## Özet
- `try/except` ile riskli kod korunur, program çökmez.
- `except:` yerine spesifik hata türü belirt.
- `else` sadece hata olmazsa, `finally` her zaman çalışır.
- `raise` ile kendi hatanı fırlatabilirsin.
