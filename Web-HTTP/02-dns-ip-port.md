---
tags: [web, http, asama-2]
ders: 2
konu: "DNS, IP ve Port"
---

# Ders 2: DNS, IP ve Port

## 1. Konunun Amacı

Bilgisayarlar isim değil, sayı anlar. Bir domain isminin gerçek bir makineye nasıl ulaştığını bilmek gerekir.

## 2. Teori

### IP Adresi

İnternetteki her cihazın (server, telefon, bilgisayar) bir **IP adresi** vardır — cihazın internet üzerindeki "fiziksel adresi".

```
192.168.1.1                          (IPv4 örneği)
2001:0db8:85a3::8a2e:0370:7334        (IPv6 örneği)
```

IPv4, 4 grup sayıdan oluşur (0-255 arası), ~4.3 milyar adres verir — yetersiz kaldığı için IPv6 geliştirildi.

### DNS (Domain Name System) — İnternetin Telefon Rehberi

DNS, **isimleri IP adreslerine çeviren dağıtık bir sistemdir.**

```
sen: "google.com'un IP'si nedir?"
DNS: "142.250.187.78"
```

**Neden isim kullanılır, direkt IP kullanılmaz?**
- IP adresleri değişebilir (server taşınabilir) ama isim (domain) sabit kalır.
- İsimler insan için hatırlanabilir, sayılar değil.

Not: Aynı kök domain altındaki subdomain'ler (`api.`, `raw.`, `gist.` gibi) genelde **farklı IP'lere** çözümlenir, çünkü farklı görevler için farklı sunucu gruplarında/altyapılarda barındırılırlar (örn. ana web sitesi ile API servisi ayrı ölçeklenir).

### Port Nedir?

Bir server'ın tek bir IP adresi olabilir, ama üzerinde aynı anda birden fazla servis çalışabilir. Bunları ayırmak için **port** kullanılır.

```
192.168.1.10:80    → web sunucusu (port 80)
192.168.1.10:5432  → PostgreSQL veritabanı (port 5432)
192.168.1.10:8000  → FastAPI uygulaması (geliştirmede yaygın)
```

**Benzetme:** IP adresi bir apartmanın adresi, port ise o apartmandaki daire numarasıdır.

**Yaygın portlar:**
- `80` → HTTP
- `443` → HTTPS
- `5432` → PostgreSQL
- `3306` → MySQL
- `22` → SSH
- `8000` / `8080` → geliştirme ortamında yaygın (FastAPI/Django)

## 3. Gerçek Dünya Bağlantısı

```bash
uvicorn main:app --port 8000
```

Bu komut "uygulamamı 8000 numaralı portta çalıştır" demektir. `http://127.0.0.1:8000` yazıldığında, `127.0.0.1` (localhost = kendi bilgisayarın) IP'sinin 8000 portundaki servise bağlanılır.

Production'da genelde `443` (HTTPS) portu kullanılır ve domain, DNS üzerinden gerçek server IP'sine çözümlenir.

## 4. Kod Örneği

```python
import socket

ip_adresi = socket.gethostbyname("github.com")
print(ip_adresi)
```

## Özet / Kritik Nokta

- DNS: isim → IP çevirisi yapar.
- IP: makinenin adresi.
- Port: o makinedeki hangi servise gidileceği.
- `ping`, `nslookup` gibi araçlar DNS çözümlemesini ve bağlantı erişilebilirliğini test etmek için kullanılır.

## İlgili Notlar
- [[01-internet-nasil-calisir-client-server|İnternet Nasıl Çalışır?]]
- [[03-tcp|TCP]]
