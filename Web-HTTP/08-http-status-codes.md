---
tags: [web, http, asama-2]
ders: 8
konu: "HTTP Status Codes"
---

# Ders 8: HTTP Status Codes

## 1. Konunun Amacı

Status code'lar rastgele değil — her biri belirli bir anlam taşıyan uluslararası standart bir sistemin parçası. FastAPI'de her endpoint'ten doğru status code döndürmek iyi API tasarımının temelidir.

## 2. Teori — 5 Kategori

**1xx — Bilgilendirme** (günlük kullanımda nadiren görülür)

**2xx — Başarılı**
```
200 OK                  → istek başarılı, genel amaçlı
201 Created             → yeni bir kaynak başarıyla oluşturuldu (POST sonrası)
204 No Content          → istek başarılı ama geri döndürecek veri yok (DELETE sonrası sık kullanılır)
```

**3xx — Yönlendirme**
```
301 Moved Permanently   → kaynak kalıcı olarak taşındı
304 Not Modified        → kaynak değişmemiş, cache'teki hali kullanılsın
```

**4xx — Client Hatası (isteği gönderen taraf hata yaptı)**
```
400 Bad Request         → isteğin formatı/içeriği hatalı
401 Unauthorized        → kimlik doğrulama gerekli ama sağlanmamış/geçersiz
403 Forbidden           → kimlik biliniyor ama işlem için yetki yok
404 Not Found           → istenen kaynak bulunamadı
409 Conflict            → istek, kaynağın mevcut durumuyla çelişiyor
422 Unprocessable Entity → format doğru ama veri validasyonu başarısız (FastAPI + Pydantic'te sık görülür)
429 Too Many Requests   → rate limit aşıldı
```

**5xx — Server Hatası (sunucu tarafında bir şeyler bozuldu)**
```
500 Internal Server Error → sunucuda beklenmeyen hata (genelde bug)
502 Bad Gateway           → sunucunun arkasındaki başka bir servis cevap vermedi
503 Service Unavailable   → sunucu şu an isteği karşılayamıyor
```

## 3. 401 vs 403 — En Çok Karıştırılan İkili

- **401 Unauthorized**: "Sen kimsin, bilmiyorum" — kimlik doğrulama eksik/geçersiz (token yok, yanlış şifre).
- **403 Forbidden**: "Sen kimsin biliyorum, ama bu işlemi yapamazsın" — kimlik doğrulandı ama yetki (permission) yok.

**Örnek:** Giriş yapmadan admin paneline gitmeye çalışmak → **401**. Giriş yapılmış ama admin değil, admin paneline gitmeye çalışmak → **403**.

## 4. Gerçek Dünya Bağlantısı

```python
from fastapi import FastAPI, HTTPException

app = FastAPI()

@app.get("/users/{user_id}")
def get_user(user_id: int):
    if user_id not in fake_db:
        raise HTTPException(status_code=404, detail="Kullanıcı bulunamadı")
    return fake_db[user_id]

@app.post("/users", status_code=201)
def create_user(user: dict):
    return {"message": "Kullanıcı oluşturuldu"}
```

Doğru status code döndürmek önemlidir çünkü client tarafı (frontend, mobil uygulama) davranışını buna göre şekillendirir: `401` alındığında login sayfasına yönlendirilir, `404` alındığında "bulunamadı" mesajı gösterilir, `500` alındığında "tekrar deneyin" denir.

## 5. Kod Örneği

```python
import requests

r = requests.get("https://api.github.com/repos/bu-repo-yok-12345/hicbiryerde")
print(r.status_code)  # 404

r = requests.get("https://api.github.com/repos/python/cpython")
print(r.status_code)  # 200
```

## Kritik Nokta — Senaryo Analizi

- **Zaten kullanılan email ile kayıt olma girişimi** → `409 Conflict` (kaynak, mevcut durumla çelişiyor) — bazı ekipler `400 Bad Request` da kullanabilir, ama semantik olarak en doğru seçim `409`'dur.
- **Giriş yapmış ama admin yetkisi olmayan kullanıcının `/admin/users`'a erişmesi** → `403 Forbidden` — çünkü kimlik zaten doğrulanmış (401 değil), sorun yetki eksikliği.

## İlgili Notlar
- [[04-http-nedir|HTTP Nedir?]]
- [[06-http-methods|HTTP Methods]]
- [[07-http-headers|HTTP Headers]]
