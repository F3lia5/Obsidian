---
tags: [web, http, asama-2]
ders: 6
konu: "HTTP Methods (GET, POST, PUT, PATCH, DELETE)"
---

# Ders 6: HTTP Methods (GET, POST, PUT, PATCH, DELETE)

## 1. Konunun Amacı

FastAPI'de yazılacak her endpoint bir HTTP method'una sahiptir (`@app.get(...)`, `@app.post(...)` gibi). Bu method'ların ne zaman kullanılacağını bilmeden doğru API tasarımı yapılamaz.

## 2. Teori

HTTP method'u isteğin **niyetini** belirtir.

### GET — Veri Oku
```
GET /users/5   → 5 numaralı kullanıcıyı getir
```
- Body taşımaz.
- **Idempotent**: Aynı isteği kaç kere atarsan at, sunucuda hiçbir şey değişmez.
- Cache'lenebilir.

### POST — Yeni Kaynak Oluştur
```
POST /users   Body: {"name": "Ahmet", "email": "ahmet@mail.com"}
```
- Body içinde veri taşır.
- **Idempotent değildir**: Aynı isteği 3 kere atarsan 3 farklı kayıt oluşabilir.

### PUT — Kaynağın TAMAMINI Güncelle
```
PUT /users/5   Body: {"name": "Ahmet", "email": "yeni@mail.com", "age": 30}
```
- **Idempotent**: Kaç kere atarsan at sonuç aynıdır.
- Eksik gönderilen alanlar genelde boşaltılır/sıfırlanır (tam güncelleme beklenir).

### PATCH — Kaynağın SADECE Belirtilen Kısmını Güncelle
```
PATCH /users/5   Body: {"email": "yeni@mail.com"}
```
- Kısmi güncelleme için tasarlanmıştır.
- Pratikte genelde idempotent şekilde tasarlanır.

### DELETE — Kaynağı Sil
```
DELETE /users/5
```
- **Idempotent**: Sildikten sonra tekrar DELETE istersen kaynak zaten yok, sistem durumu değişmez (genelde 404 döner).

## 3. PUT vs PATCH — En Çok Karıştırılan Ayrım

Kayıt: `{"id": 5, "name": "Ahmet", "email": "ahmet@mail.com", "age": 30}`

Sadece email değiştirmek isteniyor:
- **PATCH**: `{"email": "yeni@mail.com"}` → sadece email değişir, diğerleri kalır.
- **PUT**: Sadece `{"email": "yeni@mail.com"}` gönderilirse, doğru kullanımda `name` ve `age` **boş/null** yapılabilir — çünkü PUT "kaynağın yeni hali tamamen budur" demektir. PUT ile kısmi güncelleme için mevcut tüm alanlar tekrar gönderilmelidir.

## 4. Gerçek Dünya Bağlantısı

```
GET    /products          → ürün listesini getir
GET    /products/42       → 42 numaralı ürünü getir
POST   /products          → yeni ürün oluştur
PUT    /products/42       → tüm bilgilerini değiştir
PATCH  /products/42       → sadece fiyatını güncelle
DELETE /products/42       → ürünü sil
```

Çoğu gerçek API'de **PATCH, PUT'tan çok daha sık kullanılır** çünkü genelde kısmi güncelleme ihtiyacı olur.

## 5. Kod Örneği

```python
import requests

r = requests.get("https://jsonplaceholder.typicode.com/posts/1")
r = requests.post("https://jsonplaceholder.typicode.com/posts", json={"title": "Benim Postum", "body": "İçerik", "userId": 1})
r = requests.patch("https://jsonplaceholder.typicode.com/posts/1", json={"title": "Güncellenmiş Başlık"})
r = requests.delete("https://jsonplaceholder.typicode.com/posts/1")
```

## Kritik Nokta

- `POST` başarılı olduğunda genelde `201 Created` döner, `GET` ise `200 OK` (bkz. [[08-http-status-codes|HTTP Status Codes]]).
- Sadece "profil fotoğrafı" gibi tek bir alanı güncelleyen bir endpoint için **PATCH** tercih edilir — PUT kullanmak, diğer alanların yanlışlıkla sıfırlanma riskini taşır.

## İlgili Notlar
- [[04-http-nedir|HTTP Nedir?]]
- [[08-http-status-codes|HTTP Status Codes]]
