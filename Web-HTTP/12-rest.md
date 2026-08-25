---
tags: [web, http, asama-2]
ders: 12
konu: "REST"
---

# Ders 12: REST

## 1. Konunun Amacı

FastAPI ile "REST API" yazacaksın. Ama REST bir teknoloji ya da kütüphane değil — bir **mimari stil**dir, yani API tasarlarken uyulması gereken bir kurallar/prensipler bütünüdür. AŞAMA 8'de gerçek bir REST API tasarlarken bu prensipler doğrudan işine yarayacak.

## 2. Teori

**REST (Representational State Transfer)**, bir API'nin nasıl organize edilmesi gerektiğine dair bir dizi prensiptir. Bu prensiplere uyan API'lere "RESTful API" denir.

### Temel REST Prensipleri

**1. Kaynak (Resource) Tabanlı Düşünme**

REST'te her şey bir **kaynak**tır ve her kaynağın bir **URL**'i (adresi) vardır:
```
/users          → kullanıcılar kaynağı
/users/5        → 5 numaralı kullanıcı kaynağı
/products/42    → 42 numaralı ürün kaynağı
```
URL'ler **isim** (noun) içerir, **fiil** (verb) içermez. Yani `/getUser` veya `/createProduct` gibi bir tasarım REST'e aykırıdır — çünkü "ne yapılacağı" zaten [[06-http-methods|HTTP method]] ile belirtilir:
```
❌ GET /getUser/5
✅ GET /users/5

❌ POST /createUser
✅ POST /users
```

**2. HTTP Method'ları Doğru Kullanmak**

Kaynak üzerinde yapılacak işlem, URL'de değil, [[06-http-methods|HTTP method]]'unda belirtilir:
```
GET    /users/5   → getir
PUT    /users/5   → tamamen güncelle
PATCH  /users/5   → kısmen güncelle
DELETE /users/5   → sil
```

**3. Stateless Olmak**

REST API'ler [[04-http-nedir|HTTP'nin stateless]] doğasına uyar — her istek kendi içinde eksiksiz olmalı, server bir önceki isteği hatırlamamalı. (Authentication bilgisi her istekte ayrıca gönderilir — genelde bir token ile.)

**4. Standart Formatlar Kullanmak**

Veri alışverişi genelde [[11-json|JSON]] formatında yapılır (XML de kullanılabilir ama JSON günümüzde standart haline geldi).

**5. Doğru Status Code'lar Döndürmek**

[[08-http-status-codes|HTTP Status Codes]] anlamlı şekilde kullanılmalı — her şeye `200` dönmek REST prensiplerine aykırıdır.

### REST'in Getirdiği Fayda: Öngörülebilirlik

REST'e uyan bir API'yi ilk kez gören bir developer bile URL yapısına bakarak ne olduğunu tahmin edebilir:
```
GET    /orders/12/items       → 12 numaralı siparişin ürünlerini getir
POST   /orders/12/items       → 12 numaralı siparişe yeni ürün ekle
DELETE /orders/12/items/3     → 12 numaralı siparişteki 3 numaralı ürünü sil
```
Bu, ekip içi tutarlılık ve dış geliştiricilerin (varsa) API'yi kolayca öğrenmesi için kritiktir.

## 3. Gerçek Dünya Bağlantısı

Neredeyse her modern backend (Twitter/X API, GitHub API, Stripe API) REST prensiplerine (tam olarak değilse de büyük ölçüde) uyar. Şu ana kadar denediğin `api.github.com` ve `jsonplaceholder.typicode.com` da REST tasarımına örnektir — `/repos/{owner}/{repo}` gibi kaynak tabanlı URL yapısını hatırla.

## Kritik Nokta

REST, katı bir standart değil, bir **stil rehberidir** — bazı kurallara %100 uymayan API'ler de "RESTful" olarak adlandırılabilir. Önemli olan, ekibin/sistemin tutarlı bir mantık izlemesidir. AŞAMA 8'de gerçek kaynaklarla (Users, Products, Orders) tam bir REST API tasarımı yapılacak.

## İlgili Notlar
- [[06-http-methods|HTTP Methods]]
- [[08-http-status-codes|HTTP Status Codes]]
- [[11-json|JSON]]
- [[13-api|API]]
