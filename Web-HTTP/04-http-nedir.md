---
tags: [web, http, asama-2]
ders: 4
konu: "HTTP Nedir? Request / Response Yapısı"
---

# Ders 4: HTTP Nedir? Request / Response Yapısı

## 1. Konunun Amacı

TCP, veriyi güvenilir taşımayı garanti eder ama "ne taşındığını" tanımlamaz. Bunu HTTP tanımlar. FastAPI'de yazılacak her endpoint, aslında bir HTTP isteğine nasıl cevap verileceğini tanımlamaktan ibarettir.

## 2. Teori

**HTTP (HyperText Transfer Protocol)**, client ve server'ın anlaşabilmesi için ortak bir format/dildir.

### HTTP "Stateless" (Durumsuz) Bir Protokoldür

Server, bir önceki isteği **hatırlamaz**. Her HTTP isteği kendi içinde eksiksiz olmalıdır. Bu yüzden ileride "session" ve "cookie" gibi mekanizmalara ihtiyaç duyulur — server'a "hatırlama" yeteneği kazandırmak için.

Not: HTTPS ile stateless olma durumu birbirinden bağımsızdır — HTTPS sadece şifreleme sağlar, sunucunun hafızasızlığını çözmez. Bunu çözen mekanizma cookie/session/token sistemleridir (AŞAMA 9 - Authentication'da işlenecek).

### HTTP İsteği (Request) Yapısı

```
GET /repos/octocat/hello-world HTTP/1.1
Host: api.github.com
User-Agent: python-requests/2.31.0
Accept: application/json
```

- **`GET`** → HTTP method (ne yapmak istediği) → bkz. [[06-http-methods|HTTP Methods]]
- **`/repos/octocat/hello-world`** → path (hangi kaynağın istendiği)
- **`HTTP/1.1`** → kullanılan HTTP versiyonu
- **`Host`, `User-Agent`, `Accept`** → header'lar → bkz. [[07-http-headers|HTTP Headers]]

### HTTP Cevabı (Response) Yapısı

```
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 530

{"name": "hello-world", "owner": "octocat", ...}
```

- **`200 OK`** → status code → bkz. [[08-http-status-codes|HTTP Status Codes]]
- **`Content-Type`, `Content-Length`** → header'lar
- Boş satırdan sonrası → **body** (gerçek veri)

## 3. Gerçek Dünya Bağlantısı

```python
@app.get("/users/{user_id}")
def get_user(user_id: int):
    return {"user_id": user_id, "name": "Ahmet"}
```

Bir client `GET /users/5` isteği attığında, FastAPI isteği HTTP formatında alır, fonksiyonu çalıştırır, dönen veriyi JSON'a çevirip `200 OK` status code'uyla birlikte HTTP cevabı olarak geri gönderir. FastAPI, ham HTTP metnini oluşturma/parse etme işini otomatikleştirir.

## 4. Kod Örneği

```python
import requests

response = requests.get("https://api.github.com/repos/python/cpython")

print("İstek edilen URL:", response.url)
print("Status code:", response.status_code)
print("Content-Type header:", response.headers["Content-Type"])
print("Body (JSON):", response.json()["full_name"])

# Gönderilen isteğin kendisini incelemek
print("İstek metodu:", response.request.method)
print("İstek header'ları:", response.request.headers)
```

## Kritik Nokta

- `User-Agent` header'ı, isteği kimin/neyin gönderdiğini server'a bildirir (bkz. [[07-http-headers|HTTP Headers]]).
- HTTP'nin stateless olması, bir kullanıcının "giriş yapmış" bilgisinin her istekte hatırlanmaması demektir — bu problem cookie/session/token ile çözülür.

## İlgili Notlar
- [[03-tcp|TCP]]
- [[05-https|HTTPS]]
- [[06-http-methods|HTTP Methods]]
- [[07-http-headers|HTTP Headers]]
- [[08-http-status-codes|HTTP Status Codes]]
