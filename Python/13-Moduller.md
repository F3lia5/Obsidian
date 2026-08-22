#python #moduller

# Modüller

## Amaç
Kodu parçalara ayırmak ve Python'ın hazır sunduğu binlerce işlevi (dosya işlemleri, matematik, rastgele sayı üretimi vs.) kullanabilmek.

## Modül Nedir?
İçinde Python kodu olan bir `.py` dosyası, başka bir dosyadan çağrılabilir hale gelmiş şeklidir. Python'ın **standart kütüphane** modülleri (`math`, `random`, `datetime` gibi) zaten kurulu gelir, sadece `import` etmek yeterli.

## `import` Kullanımı

```python
import math

print(math.sqrt(16))     # 4.0  (karekök)
print(math.pi)             # 3.14159...
```

Belirli bir şeyi modülden almak:
```python
from math import sqrt

print(sqrt(16))    # artık math. yazmaya gerek yok
```

Takma isim vermek:
```python
import math as m
print(m.sqrt(16))
```

## Kendi Modülünü Oluşturmak

```python
# araclar.py
def kare_al(x):
    return x ** 2
```

```python
# ana.py
import araclar

print(araclar.kare_al(5))   # 25
```

Bu, tekrar kullanılabilecek fonksiyonları (örneğin `calculate()` gibi) ayrı bir dosyaya taşıyıp farklı projelerde kullanabilmek anlamına gelir.

## Sık Kullanılan Standart Kütüphane Modülleri (önizleme)

```python
import random
print(random.randint(1, 10))   # 1-10 arası rastgele tam sayı

import datetime
print(datetime.datetime.now())  # şu anki tarih/saat
```

## Görsel Mantık

```
   ana.py                    araclar.py
┌──────────────┐          ┌─────────────────┐
│ import araclar│ ───────► │ def kare_al(x): │
│               │          │     return x**2 │
│ araclar.      │          └─────────────────┘
│  kare_al(5)   │
└──────────────┘
```

## Yaygın Hatalar
- `from math import *` kullanmak → modüldeki HER şeyi isim çakışması riskiyle içeri alır, hangi fonksiyonun nereden geldiği belirsizleşir (PEP 8'e aykırı)
- Modül adını değişken adıyla çakıştırmak (örn. `math = 5` demek, sonra `math` modülüne erişememek)
- Kendi dosyanı yanlış konumdan import etmeye çalışmak (aynı klasörde ya da `sys.path` içinde olmalı)

## Best Practice
- `from module import *` yerine `import module` ya da `from module import belirli_fonksiyon` kullan
- İlgili fonksiyonları mantıklı gruplar halinde ayrı dosyalara (modüllere) böl

## Özet
- `import module` → `module.fonksiyon()` şeklinde erişim.
- `from module import fonksiyon` → modül adı yazmadan doğrudan kullanım.
- Kendi `.py` dosyaların da modül gibi `import` edilebilir — kodu düzenli parçalara ayırmanın temeli.
- `from module import *` önerilmez.
