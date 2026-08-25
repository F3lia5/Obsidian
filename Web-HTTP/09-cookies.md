---
tags: [web, http, asama-2]
ders: 9
konu: "Cookies"
---

# Ders 9: Cookies

## 1. Konunun Amacı

HTTP'nin stateless (durumsuz) olduğunu öğrendik — server hiçbir isteği hatırlamaz. Ama gerçek hayatta bir kullanıcı bir siteye giriş yaptığında, her sayfa değişiminde tekrar login istenmez. Bu "hatırlama" ihtiyacını çözen ilk mekanizma cookie'lerdir.

## 2. Teori

**Cookie**, server'ın tarayıcıya gönderdiği, tarayıcının **her sonraki istekte otomatik olarak server'a geri gönderdiği** küçük bir veri parçasıdır (genelde birkaç KB'lık metin).

### Nasıl Çalışır?

1. Client bir isteği atar.
2. Server cevap header'ında `Set-Cookie` ile bir cookie gönderir:
```
HTTP/1.1 200 OK
Set-Cookie: session_id=abc123; HttpOnly; Secure; SameSite=Strict
```
3. Tarayıcı bu cookie'yi kaydeder.
4. Aynı domaine yapılan **her sonraki istekte**, tarayıcı bu cookie'yi otomatik olarak `Cookie` header'ı ile geri gönderir:
```
GET /profil HTTP/1.1
Cookie: session_id=abc123
```
5. Server, gelen cookie'ye bakarak "bu isteği kim atıyor" bilgisini çözer.

### Önemli Cookie Özellikleri (Attribute'lar)

- **`HttpOnly`** → Cookie'ye JavaScript'ten erişilemez, sadece HTTP istekleri taşıyabilir. XSS saldırılarına karşı önemli bir korumadır.
- **`Secure`** → Cookie sadece HTTPS bağlantılarda gönderilir, şifresiz HTTP üzerinden asla gitmez.
- **`SameSite`** → Cookie'nin başka sitelerden gelen isteklerle gönderilip gönderilmeyeceğini kontrol eder (CSRF saldırılarına karşı koruma sağlar — AŞAMA 9'da detaylandırılacak).
- **`Expires` / `Max-Age`** → Cookie'nin ne zaman geçersiz olacağı. Belirtilmezse "session cookie" olur — tarayıcı kapatılınca silinir.

## 3. Gerçek Dünya Bağlantısı

Cookie'ler login sistemlerinde, kullanıcı tercihlerini hatırlamada (dil, tema), ve reklam takibinde (bu daha çok gizlilik tartışmalarına konu olur) kullanılır.

FastAPI'de cookie ile çalışmak:
```python
from fastapi import FastAPI, Response, Cookie

app = FastAPI()

@app.post("/login")
def login(response: Response):
    response.set_cookie(key="session_id", value="abc123", httponly=True, secure=True)
    return {"message": "Giriş başarılı"}

@app.get("/profil")
def profil(session_id: str = Cookie(None)):
    return {"gelen_session_id": session_id}
```

## Kritik Nokta

Cookie, tek başına bir güvenlik mekanizması değildir — içine hassas veri (parola, kredi kartı) **doğrudan** koymak büyük bir hatadır. Genelde içine sadece bir **session ID** (rastgele, anlamsız bir kimlik) konur, gerçek veri server tarafında saklanır. Bu yaklaşım bir sonraki dersin (Sessions) konusudur.

## İlgili Notlar
- [[04-http-nedir|HTTP Nedir?]]
- [[07-http-headers|HTTP Headers]]
- [[10-sessions|Sessions]]
