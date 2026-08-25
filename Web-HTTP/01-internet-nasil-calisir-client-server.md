---
tags: [web, http, asama-2]
ders: 1
konu: "İnternet Nasıl Çalışır? Client / Server Mimarisi"
---

# Ders 1: İnternet Nasıl Çalışır? Client / Server Mimarisi

## 1. Konunun Amacı

FastAPI ile bir backend yazmadan önce "backend" ne demek, kiminle konuşuyor, o konuşma fiziksel olarak nasıl gerçekleşiyor — bunu anlamak gerekir. Aksi halde yazılan kod sihir gibi kalır.

## 2. Teori

### Client / Server Modeli

- **Client (istemci)**: İsteği başlatan taraf. Tarayıcı, mobil uygulama, ya da bir Python scripti.
- **Server (sunucu)**: İsteği bekleyen, karşılayan ve cevap veren taraf. İleride yazılacak FastAPI uygulaması bir server'dır.

```
Client                          Server
(Tarayıcı)  ---- İstek gönderir ---->  (FastAPI uygulaması)
            <---- Cevap döner ------
```

**Kritik nokta:** Server her zaman pasiftir. Kendiliğinden bir şey yapmaz, sadece gelen isteklere cevap verir. Client her zaman inisiyatifi alan taraftır.

### Bir İsteğin Fiziksel Yolculuğu

1. Tarayıcı, domaini gerçek bir makinenin adresine çevirmesi gerektiğini bilir → bkz. [[02-dns-ip-port|DNS, IP ve Port]]
2. IP adresi bulunduktan sonra o adresteki makineyle bir bağlantı kurulur → bkz. [[03-tcp|TCP]]
3. Bağlantı kurulduktan sonra "bana şu sayfayı gönder" isteği gönderilir → bkz. [[04-http-nedir|HTTP Nedir]]
4. Eğer bağlantı şifreliyse bu aşamada ek bir güvenlik katmanı devreye girer → bkz. [[05-https|HTTPS]]
5. Server isteği işler, bir cevap üretir; bu cevabın "ne anlama geldiği" [[08-http-status-codes|HTTP Status Codes]] ile, "ek bilgileri" ise [[07-http-headers|HTTP Headers]] ile taşınır.
6. İsteğin **niyeti** ([[06-http-methods|HTTP Methods]]) her zaman bellidir: okumak mı, oluşturmak mı, güncellemek mi, silmek mi.

### Neden Bu Mimari Böyle Tasarlandı?

Client-server modeli şunu sağlar:
- **Merkezi kontrol**: Veriler tek bir yerde (server'da) tutulur, tutarlılık sağlanır.
- **Güvenlik**: Client'lar direkt birbirine erişemez, her şey server üzerinden kontrollü geçer.
- **Ölçeklenebilirlik**: Server güçlendirilerek/çoğaltılarak binlerce client'a aynı anda hizmet verilebilir.

## 3. Gerçek Dünya Bağlantısı

Yazılacak her FastAPI uygulaması bir **server**'dır. Kullanıcının tarayıcısı, mobil uygulaması veya başka bir backend servisi — hepsi bu API'ya **client** olarak istek atar.

Örnek (e-ticaret sitesi):
- Tarayıcı (client) → "ürün listesini göster" isteği gönderir
- FastAPI backend (server) → veritabanından ürünleri çeker, JSON olarak döner
- Tarayıcı bu JSON'u alıp ekranda gösterir

## 4. Kod Örneği

```python
import requests  # bir CLIENT kütüphanesi

response = requests.get("https://api.github.com")

print(response.status_code)  # server'ın döndürdüğü durum kodu -> bkz. HTTP Status Codes
print(response.json())       # server'ın döndürdüğü veri
```

## Özet / Kritik Nokta

- Bu 3 satırlık kodun arkasında: DNS çözümleme → TCP bağlantısı → (varsa TLS/HTTPS el sıkışması) → HTTP isteği → HTTP cevabı zinciri çalışır.
- Python scripti burada **client**, `api.github.com` ise **server**'dır — isteği başlatan taraf her zaman client'tır.

## İlgili Notlar
- [[02-dns-ip-port|DNS, IP ve Port]]
- [[03-tcp|TCP]]
- [[04-http-nedir|HTTP Nedir? Request / Response Yapısı]]
- [[05-https|HTTPS]]
- [[06-http-methods|HTTP Methods]]
- [[07-http-headers|HTTP Headers]]
- [[08-http-status-codes|HTTP Status Codes]]
- [[09-cookies|Cookies]]
- [[10-sessions|Sessions]]
- [[11-json|JSON]]
- [[12-rest|REST]]
- [[13-api|API Nedir?]]
