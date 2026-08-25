---
tags: [web, http, asama-2]
ders: 13
konu: "API Nedir?"
---

# Ders 13: API Nedir?

## 1. Konunun Amacı

Bu aşama boyunca sürekli "API" kelimesini kullandık. Artık bu kelimenin altını dolduracak tüm parçalar (client/server, HTTP, JSON, REST) elinde — şimdi hepsini birleştirip "API" kavramını netleştirme zamanı.

## 2. Teori

**API (Application Programming Interface)**, iki yazılımın birbiriyle **belirlenmiş kurallar çerçevesinde konuşabilmesini** sağlayan arayüz/sözleşmedir.

**Benzetme:** Bir restoranda garson, API gibi düşünülebilir. Sen (client) mutfağa (server) direkt giremezsin, ne olduğunu bilemezsin. Garsona (API) menüden bir şey söylersin, garson mutfağa iletir, sana yemeği (response) getirir. Menü, "hangi isteği yapabileceğini" (hangi endpoint'lerin var olduğunu) tanımlar.

### Bir Web API'si Somut Olarak Nedir?

Şimdiye kadar öğrendiğin her şeyin toplamı bir Web API'sidir:
- Belirli **URL'ler** (endpoint'ler) tanımlanır → [[12-rest|REST]] prensiplerine göre kaynak bazlı
- Bu URL'lere belirli **HTTP method'ları** ile istek atılır → [[06-http-methods|HTTP Methods]]
- İstek ve cevaplar genelde **JSON** formatındadır → [[11-json|JSON]]
- Her cevap bir **status code** ile birlikte gelir → [[08-http-status-codes|HTTP Status Codes]]
- Kimlik doğrulama gerekiyorsa **header'lar** (Authorization) kullanılır → [[07-http-headers|HTTP Headers]]

```
API = URL yapısı + HTTP method'ları + Request/Response formatı (JSON) + Status code'lar + Authentication kuralları
```

### API Türleri (Kısaca)

- **Web API / REST API** — HTTP üzerinden çalışan, bu aşamada öğrendiğimiz tür (FastAPI ile bunu yazacaksın).
- **Kütüphane/Framework API'si** — Bir programlama dilindeki bir kütüphanenin fonksiyonları da teknik olarak bir "API"dir (örn. `requests.get()` fonksiyonu, `requests` kütüphanesinin API'sidir). Bu, web API'sinden farklı bir kavramdır — network üzerinden değil, kod içinde çağrılır.
- **GraphQL** — REST'e alternatif bir API sorgu dili (şimdilik bilgi olarak yeter, backend temelini tamamladıktan sonra istersen ayrıca bakılabilir).

## 3. Gerçek Dünya Bağlantısı

Şu ana kadar yaptığın her `requests.get(...)` çağrısı, gerçekte bir **API tüketimiydi** (consuming an API):
- `api.github.com` → GitHub'ın sunduğu bir API
- `jsonplaceholder.typicode.com` → test amaçlı sahte bir API

AŞAMA 4'te (FastAPI) sen artık bu API'leri **tüketen** değil, **sunan** taraf olacaksın — kendi API'ni yazıp, başkalarının (frontend, mobil uygulama, başka backend'ler) senin API'ne istek atmasını sağlayacaksın.

### API Dokümantasyonu

Gerçek bir API'nin nasıl kullanılacağını anlatan bir dokümantasyonu olur — hangi endpoint'ler var, hangi parametreleri alıyor, ne döndürüyor. FastAPI'nin en güçlü özelliklerinden biri, bu dokümantasyonu **otomatik olarak** oluşturmasıdır (Swagger UI) — bunu AŞAMA 4'te göreceksin.

## Kritik Nokta — AŞAMA 2 Özeti

Bu aşamada öğrendiklerin, aslında birbirinin üzerine inşa olan tek bir zincirdi:

```
DNS/IP/Port (adres bulma)
    ↓
TCP (güvenilir bağlantı kurma)
    ↓
HTTPS (bağlantıyı şifreleme)
    ↓
HTTP (client-server konuşma dili: method, header, status code)
    ↓
JSON (konuşulan verinin formatı)
    ↓
REST (bu konuşmanın nasıl organize edileceğine dair kurallar)
    ↓
API (tüm bunların bütünü — iki yazılımın anlaştığı sözleşme)
```

Bu zincirin her halkasını anladıysan, FastAPI'de yazacağın kod artık "sihir" değil, **bildiğin kavramların Python'a dökülmüş hali** olacak.

## İlgili Notlar
- [[12-rest|REST]]
- [[11-json|JSON]]
- [[01-internet-nasil-calisir-client-server|İnternet Nasıl Çalışır?]]
