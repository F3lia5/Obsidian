---
tags: [web, http, asama-2]
ders: 11
konu: "JSON"
---

# Ders 11: JSON

## 1. Konunun Amacı

Şimdiye kadar tüm örneklerde `response.json()` çağırdık, body'lerin `{"name": "Ahmet"}` gibi göründüğünü gördük. JSON, backend dünyasının ortak veri dilidir — FastAPI'de neredeyse her şey JSON olarak gidip gelir.

## 2. Teori

**JSON (JavaScript Object Notation)**, verinin **metin tabanlı, hem insan hem makine tarafından kolay okunabilen** bir formatta temsil edilmesidir. Adında "JavaScript" geçse de, artık dilden bağımsız evrensel bir standarttır — Python, Java, Go, her dil JSON okuyup yazabilir.

### JSON Veri Tipleri

```json
{
  "isim": "Ahmet",              // string (metin)
  "yas": 30,                    // number (sayı)
  "aktif_mi": true,              // boolean
  "adres": null,                 // null (boş değer)
  "hobiler": ["kitap", "spor"],  // array (liste)
  "profil": {                    // object (iç içe obje)
    "sehir": "İstanbul"
  }
}
```

### Python ile JSON İlişkisi

Python'ın kendi veri yapıları JSON'a çok benzer, bu yüzden dönüşüm kolaydır:

| Python | JSON |
|---|---|
| `dict` | object `{}` |
| `list` | array `[]` |
| `str` | string |
| `int` / `float` | number |
| `True` / `False` | true / false |
| `None` | null |

```python
import json

# Python dict -> JSON string
veri = {"isim": "Ahmet", "yas": 30, "aktif": True}
json_metni = json.dumps(veri)
print(json_metni)  # '{"isim": "Ahmet", "yas": 30, "aktif": true}'
print(type(json_metni))  # <class 'str'> - artık bir metin

# JSON string -> Python dict
geri_donusum = json.loads(json_metni)
print(geri_donusum)  # {'isim': 'Ahmet', 'yas': 30, 'aktif': True}
print(type(geri_donusum))  # <class 'dict'>
```

**Kritik nokta:** JSON, ağ üzerinden gönderilirken aslında sadece bir **string** (metin)tir. `Content-Type: application/json` header'ı, alıcı tarafa "bu metni JSON olarak parse et" der.

## 3. Gerçek Dünya Bağlantısı

FastAPI'de JSON dönüşümü tamamen otomatiktir:

```python
from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI()

class Kullanici(BaseModel):
    isim: str
    yas: int

@app.post("/kullanici")
def kullanici_olustur(kullanici: Kullanici):
    return kullanici  # FastAPI bunu otomatik JSON'a çevirip döner
```

Client bir JSON body gönderdiğinde, FastAPI bunu otomatik olarak Pydantic modeline (`Kullanici`) çevirir — bu konuyu AŞAMA 4'te (FastAPI) çok detaylı işleyeceğiz.

## Kritik Nokta

JSON'da **sondan bir önceki elemandan sonra virgül konmaz** (trailing comma hatası çok yaygın bir syntax hatasıdır):
```json
{"isim": "Ahmet", "yas": 30,}   ❌ HATALI - son virgül geçersiz
{"isim": "Ahmet", "yas": 30}    ✅ DOĞRU
```
Ayrıca JSON'da key'ler (anahtar isimleri) her zaman **çift tırnak** içinde olmalıdır — tek tırnak (`'isim'`) geçersizdir, bu Python dict syntax'ı ile karışan en yaygın hatadır.

## İlgili Notlar
- [[04-http-nedir|HTTP Nedir?]]
- [[07-http-headers|HTTP Headers]]
- [[12-rest|REST]]
