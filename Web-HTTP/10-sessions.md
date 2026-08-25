---
tags: [web, http, asama-2]
ders: 10
konu: "Sessions"
---

# Ders 10: Sessions

## 1. Konunun Amacı

Cookie'nin içine doğrudan hassas veri koymak güvensizdir. Session mekanizması, gerçek veriyi server'da tutup, client'a sadece bir "kimlik kartı" vererek bu problemi çözer.

## 2. Teori

**Session**, bir kullanıcıya ait verinin **server tarafında** saklandığı, client'a ise sadece bu veriye erişim sağlayan rastgele bir kimliğin (**session ID**) cookie olarak verildiği yöntemdir.

### Nasıl Çalışır?

1. Kullanıcı giriş yapar (`POST /login`).
2. Server, bu kullanıcı için bir session oluşturur ve kendi hafızasında (veya bir veritabanında/Redis'te) saklar:
```
session_id: "abc123" -> { user_id: 5, name: "Ahmet", giris_zamani: "..." }
```
3. Server, client'a sadece `session_id=abc123` değerini cookie olarak gönderir — gerçek veri (user_id, name) client'a hiç gitmez.
4. Client, sonraki her istekte bu `session_id`'yi otomatik gönderir.
5. Server, gelen `session_id`'ye bakarak kendi hafızasındaki gerçek veriyi bulur: "Ah, bu session abc123, demek ki bu istek Ahmet'ten (user_id: 5) geliyor."

```
Client                              Server
Cookie: session_id=abc123   ---->   session_id: abc123 -> {user_id: 5, name: "Ahmet"}
                                     (server hafızasında/veritabanında saklı)
```

### Session'ın Sunucu Tarafındaki Depolanma Yerleri

- **In-memory** (RAM'de, basit projelerde) — server yeniden başlarsa tüm session'lar kaybolur, birden fazla server varsa paylaşılamaz.
- **Redis** (yaygın, production'da tercih edilir) — hızlı, dağıtık sistemlerde paylaşılabilir.
- **Veritabanı** (PostgreSQL gibi) — kalıcı ama daha yavaş.

## 3. Gerçek Dünya Bağlantısı

Session tabanlı authentication, klasik web uygulamalarında (Django gibi) çok yaygındır. Ama modern API'lerde (özellikle mobil uygulamalar, mikroservisler) **session yerine token tabanlı sistemler (JWT gibi) daha çok tercih edilir** — çünkü session, server'ın "hafızalı" (stateful) olmasını gerektirir; bu da birden fazla server arasında ölçeklenmeyi zorlaştırır. Bu farkı AŞAMA 9'da (Authentication) çok detaylı işleyeceğiz.

**Session vs Token karşılaştırması (önizleme):**

| | Session | Token (örn. JWT) |
|---|---|---|
| Veri nerede tutulur? | Server'da | Token'ın kendi içinde (şifreli/imzalı) |
| Server "hatırlamalı" mı? | Evet (stateful) | Hayır (stateless) |
| Birden fazla server'a ölçekleme | Zor (session paylaşımı gerekir) | Kolay (her server token'ı kendi doğrular) |

## Kritik Nokta

Session, HTTP'nin stateless doğasını **aşmaz** — server yine her isteği "hatırlamıyor" gibi karşılar, ama gelen `session_id` sayesinde "bu isteğin kime ait olduğunu" bir veri deposuna bakarak çözer. Yani stateless protokolün üzerine, server tarafında "hafıza" ekleyen bir katmandır.

## İlgili Notlar
- [[09-cookies|Cookies]]
- [[04-http-nedir|HTTP Nedir?]]
