---
tags: [web, http, asama-2]
ders: 5
konu: "HTTPS — HTTP'nin Şifrelenmiş Hali"
---

# Ders 5: HTTPS — HTTP'nin Şifrelenmiş Hali

## 1. Konunun Amacı

HTTP'nin verisi düz metin (plaintext) halinde gider. HTTPS bu problemi çözer. Production'da HTTPS kullanmamak ciddi bir güvenlik açığıdır.

## 2. Teori

### HTTP'nin Problemi: Düz Metin

```
GET /users/5 HTTP/1.1
Authorization: Bearer abc123...
```

Bu istek client'tan server'a giderken birden fazla ara noktadan geçer. Biri bu trafiği dinlerse (**man-in-the-middle** saldırısı), şifre, kredi kartı bilgisi, token gibi veriler olduğu gibi okunabilir.

### HTTPS'in Çözümü: TLS/SSL Şifrelemesi

HTTPS = HTTP + **TLS (Transport Layer Security)** şifrelemesi.

```
HTTP:  GET /login?password=1234        <- düz metin, herkes okuyabilir
HTTPS: 8f3a9c2e1b7d4f...                <- şifreli, sadece server çözebilir
```

### Nasıl Çalışır (Kavramsal)

1. Client, server'a bağlanmak ister.
2. Server, kendi kimliğini kanıtlayan bir **sertifika** gösterir — güvenilir bir üçüncü taraf (**Certificate Authority**, örn. Let's Encrypt) tarafından imzalanmıştır.
3. Client sertifikayı doğrular.
4. İki taraf şifreleme anahtarları üzerinde anlaşır (**TLS handshake** — TCP'nin 3-way handshake'ine benzer, şifreleme için).
5. Bundan sonraki veri alışverişi bu anahtarlarla şifrelenir.

## 3. Gerçek Dünya Bağlantısı

- Tarayıcılar `http://` sitelere "Not Secure" uyarısı gösterir.
- Google, HTTPS kullanmayan siteleri arama sonuçlarında cezalandırır.
- Login, ödeme, kişisel veri içeren her endpoint için HTTPS zorunludur.
- FastAPI, HTTPS'i doğrudan yönetmez; genelde önündeki bir **reverse proxy** (Nginx gibi) veya bulut sağlayıcı (Render, Railway, AWS) bunu sağlar. HTTPS deployment aşamasında altyapı tarafından sağlanır, kod içinde "yazılmaz".

## 4. Kod Örneği

```python
import ssl
import socket

hostname = "api.github.com"
context = ssl.create_default_context()

with socket.create_connection((hostname, 443)) as sock:
    with context.wrap_socket(sock, server_hostname=hostname) as ssock:
        cert = ssock.getpeercert()
        print("Sertifika kime ait:", cert.get('subject'))
        print("Sertifikayı kim imzalamış:", cert.get('issuer'))
        print("Geçerlilik bitiş tarihi:", cert.get('notAfter'))
```

## Kritik Nokta

- `443` portu → HTTPS trafiği için standart port (bkz. [[02-dns-ip-port|DNS, IP ve Port]]).
- HTTPS, verinin **içeriğini** şifreler ama isteğin **hangi domain'e gittiğini** tam gizlemez. Bir saldırgan hâlâ şunları görebilir:
  - Hangi domain'e bağlanıldığını (DNS sorgusu ve TLS handshake'in ilk kısmı — SNI — genelde şifrelenmemiş gider)
  - Trafiğin ne zaman, ne sıklıkla, ne büyüklükte olduğu (metadata)
  - Hangi IP'ye bağlanıldığı
- Özet: HTTPS "kiminle konuştuğunu" tam gizlemez, sadece "ne konuştuğunu" gizler.

## İlgili Notlar
- [[03-tcp|TCP]]
- [[04-http-nedir|HTTP Nedir?]]
