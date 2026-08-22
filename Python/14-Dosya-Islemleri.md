#python #dosya-islemleri

# Dosya İşlemleri (File Handling)

## Amaç
Veriyi kalıcı hale getirmek — program kapansa bile bir sonraki çalıştırmada erişilebilir olması.

## Dosya Açma — `open()`

```python
dosya = open("notlar.txt", "w")
dosya.write("Merhaba dosya!")
dosya.close()                       # KRİTİK: unutmamalı!
```

### Mod Parametreleri

| Mod | Anlamı |
|---|---|
| `"r"` | Read (okuma) — varsayılan, dosya yoksa hata verir |
| `"w"` | Write (yazma) — dosya yoksa oluşturur, **varsa içeriğini siler** |
| `"a"` | Append (ekleme) — sona ekler, mevcut içeriği silmez |
| `"r+"` | Hem okuma hem yazma |

## `with` Kullanımı — Daha Güvenli (HER ZAMAN TERCİH EDİLMELİ)

```python
with open("notlar.txt", "w") as dosya:
    dosya.write("Merhaba dosya!")
# blok bitince dosya OTOMATİK kapanır
```

> Benzetme: otomatik kapanan bir kapıdan geçmek gibi — `close()` unutma riski ortadan kalkar.

## Dosya Okuma

```python
with open("notlar.txt", "r") as dosya:
    icerik = dosya.read()        # tüm içeriği TEK STRING olarak alır
    print(icerik)                    # read() otomatik ekrana yazmaz, print gerekir!

with open("notlar.txt", "r") as dosya:
    for satir in dosya:            # satır satır okuma (büyük dosyalarda verimli)
        print(satir.strip())        # \n'i temizler
```

## Dosya Var mı Kontrolü

```python
import os
if os.path.exists("notlar.txt"):
    print("Dosya var")
```

## Görsel Mantık

```
"w" modu:                          "a" modu:
┌──────────────┐                   ┌──────────────┐
│ eski içerik  │ ──► SİLİNİR       │ eski içerik  │ ──► KORUNUR
│ yeni içerik  │                   │ + yeni içerik│ ──► sona eklenir
└──────────────┘                   └──────────────┘
```

## Yaygın Hatalar
- `close()` çağırmayı unutmak → veri kaybı riski (bu yüzden `with` tercih edilir)
- `"w"` modunu var olan bir dosyada yanlışlıkla kullanmak → içerik tamamen silinir
- Olmayan dosyayı `"r"` modunda açmak → `FileNotFoundError`
- `read()` sonucunu otomatik ekrana çıkacak sanmak → `print()` gerekir

## Best Practice
- Her zaman `with open(...) as f:` kullan
- Büyük dosyalarda `read()` yerine satır satır oku
- Hangi modu (`w` mı `a` mı) istediğinden emin ol — `w` geri dönüşsüz silme yapabilir

## Kişisel Not
`file.read()` bir string **döndürür**, otomatik ekrana yazmaz:
```python
with open("gunluk.txt", "r") as file:
    file.read()          # YANLIŞ - sonuç hiçbir yere gitmiyor
    print(file.read())    # DOĞRU
```

## Özet
- `open(dosya, mod)` — `"r"` okuma, `"w"` yazma (siler), `"a"` ekleme (korur).
- `with` dosyanın otomatik kapanmasını garanti eder.
- `read()` string döndürür, `print` ile gösterilmeli.
