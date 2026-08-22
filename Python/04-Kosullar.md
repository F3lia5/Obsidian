#python #temel #kosullar

# Koşullar (if, elif, else)

## Amaç
Programın karar vermesini sağlamak — "eğer bu doğruysa şunu yap, değilse başka bir şey yap".

## Temel Yapı

```python
if kosul:
    # kosul True ise burası çalışır
elif baska_kosul:
    # ilk kosul False, bu True ise burası çalışır
else:
    # hiçbiri True değilse burası çalışır
```

**Kurallar:**
- `if` her zaman gereklidir, `elif`/`else` isteğe bağlıdır.
- `elif` istediğin kadar tekrar edebilir, `else` en fazla bir tane, en sonda.
- Python koşulları **sırayla yukarıdan aşağıya** kontrol eder, ilk `True`'da durur, geri kalanlara bakmaz.

## Truthy / Falsy

- **Falsy:** `0`, `0.0`, `""`, `[]`, `None`, `False`
- **Truthy:** bunların dışındaki her şey

```python
isim = ""
if isim:
    print("İsim var")
else:
    print("İsim boş")   # bu çalışır, boş string falsy'dir
```

## Sıralı Kontrol — Kritik Detay

```python
sayi = 15
if sayi > 10:
    print("10'dan büyük")
elif sayi > 5:
    print("5'ten büyük")
# Çıktı: "10'dan büyük" — ikinci koşul HİÇ kontrol edilmez
```

## `elif` vs Ayrı `if`ler — Fark

```python
# elif zinciri: sadece biri çalışır
if sayi > 10: ...
elif sayi > 5: ...

# ayrı if'ler: HER İKİSİ DE bağımsız kontrol edilir, ikisi de çalışabilir
if sayi > 10: ...
if sayi > 5: ...
```

## Yaygın Hatalar
- Ayrı `if`ler kullanıp `elif` kullanmamak → beklenmeyen çoklu çıktı
- `if x == True:` yazmak → gereksiz, `if x:` yeterli
- Koşulları yanlış sırada yazmak (genel koşulu özel koşuldan önce yazmak) → özel koşula hiç ulaşılmaz

## Best Practice
- Koşulları **en özelden genele** doğru sırala
- `if x == True` yerine `if x`, `if x == False` yerine `if not x`
- Birbirini dışlayan durumlar için `elif`, bağımsız kontroller için ayrı `if`

## Kişisel Not — Üst/Alt Sınır Sadeleştirme Tuzağı
```python
# Hem üst hem alt sınır kontrolü varsa, sadeleştirirken dikkat!
if not_ > 100:
    print("Geçersiz not")
elif not_ >= 90:
    print("AA")
elif not_ >= 80:
    print("BA")
...
elif not_ >= 0:
    print("FF")
else:
    print("Geçersiz not")
```
`elif` zincirinde "önceki koşul False olduğu için tekrar kontrol etmeye gerek yok" mantığı sadece **tek yönlü** (örn. alt sınır) sadeleştirmede güvenlidir. Hem üst hem alt sınır varsa (örn. not 0-100 arası olmalı), üst sınırı **en başa** ayrı bir kontrol olarak eklemek gerekir — yoksa `150` gibi geçersiz bir değer sessizce `AA` gibi yanlış bir sonuca düşebilir.

## Özet
- `if/elif/else` ile karar verme; Python sırayla kontrol eder, ilk `True`'da durur.
- `0`, `""`, `[]`, `None`, `False` → falsy; diğerleri truthy.
- Sadeleştirme yaparken uç durumları (edge case) her zaman tekrar test et.
