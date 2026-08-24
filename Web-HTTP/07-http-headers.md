---
tags: [web, http, asama-2]
ders: 7
konu: "HTTP Headers"
---

# Ders 7: HTTP Headers

## 1. Konunun Amacı

Header'ların ne işe yaradığını bilmeden ne FastAPI'de doğru header ayarlanabilir ne de gelen isteklerden doğru bilgi çıkarılabilir.

## 2. Teori

Header'lar, bir HTTP isteği/cevabıyla birlikte giden, **body hakkında ek bilgi taşıyan** anahtar-değer çiftleridir.

**Benzetme:** Bir kargo paketinde **body** kutunun içindeki ürün, **header'lar** ise kutu üzerindeki etiketlerdir ("Kırılacak eşya", "Ağırlık: 2kg" gibi) — kutuyu açmadan bilinmesi gerekenler.

### İstek (Request) Header'ları
```
Host: api.github.com              → hangi domain'e istek atılıyor
User-Agent: python-requests/2.31  → isteği kim/ne gönderdi
Authorization: Bearer eyJhbGc...  → kimlik doğrulama bilgisi (token)
Content-Type: application/json    → gönderilen body'nin formatı
Accept: application/json          → client'ın istediği cevap formatı
```

### Cevap (Response) Header'ları
```
Content-Type: application/json    → dönen body'nin formatı
Content-Length: 530               → body'nin byte cinsinden boyutu
Set-Cookie: session_id=abc123     → server'ın client'a cookie kaydetmesi isteği
Cache-Control: max-age=60         → cevabın ne kadar süre önbelleğe alınabileceği
```

### Content-Type Neden Kritik?

Server'a gönderilen body'nin türü belirtilmezse, server onu nasıl yorumlayacağını bilemez.

```python
requests.post(url, json={"name": "Ahmet"})   # otomatik Content-Type: application/json ekler
requests.post(url, data={"name": "Ahmet"})   # Content-Type: application/x-www-form-urlencoded
```

FastAPI, `Pydantic` modeliyle body'yi parse ederken bu header'a bakarak "JSON mu, form mu?" kararını verir.

### Authorization Header'ı

```
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```

"Bearer", token tabanlı kimlik doğrulama (JWT gibi) olduğunu belirtir. Server bu token'ı doğrulayıp "bu isteği kim atıyor" bilgisini çıkarır (AŞAMA 9 - Authentication'da detaylandırılacak).

## 3. Gerçek Dünya Bağlantısı

```python
from fastapi import FastAPI, Header

app = FastAPI()

@app.get("/profil")
def profil_getir(authorization: str = Header(None)):
    return {"gelen_token": authorization}
```

CORS mekanizması da tamamen header'lar üzerinden çalışır — tarayıcı, bir isteğin başka bir domain'den gelip gelmediğini header'lara bakarak kontrol eder.

## 4. Kod Örneği

```python
import requests

headers = {
    "User-Agent": "benim-python-scriptim/1.0",
    "Accept": "application/json"
}

response = requests.get("https://api.github.com/repos/python/cpython", headers=headers)

print("Gönderdiğim header'lar:", response.request.headers)
print("Gelen Content-Type:", response.headers.get("Content-Type"))
```

## Kritik Nokta

- `requests.post(url, json=...)` çağrıldığında kütüphane otomatik olarak `Content-Type: application/json` header'ını ekler — server, body'yi bu sayede doğru parse eder.
- `User-Agent` header'ı, sitelerin bir isteğin gerçek bir tarayıcıdan mı yoksa bir script/bottan mı geldiğini ayırt etmesine yardımcı olur (bot engelleme, scraping tespiti gibi senaryolarda kullanılır).

## İlgili Notlar
- [[04-http-nedir|HTTP Nedir?]]
- [[08-http-status-codes|HTTP Status Codes]]
