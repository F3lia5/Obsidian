---
tags: [web, http, asama-2]
ders: 3
konu: "TCP — Bağlantı Nasıl Kurulur?"
---

# Ders 3: TCP — Bağlantı Nasıl Kurulur?

## 1. Konunun Amacı

IP adresini bilmek, o makineyle güvenilir veri alışverişi yapabilmek anlamına gelmez. TCP, bu güvenilir bağlantıyı kuran protokoldür.

## 2. Teori

**TCP (Transmission Control Protocol)**, verinin eksiksiz ve doğru sırada ulaşmasını garanti eden bir protokoldür.

Veri gönderilirken küçük parçalara (**paket**) bölünür. Paketler farklı yollardan gidebilir, sırası karışabilir, kaybolabilir. TCP bunu şöyle çözer:
- Her pakete bir sıra numarası verir.
- Karşı taraf paketi aldığını onaylar (**ACK**).
- Kaybolan paket fark edilip yeniden gönderilir.
- Tüm paketler doğru sırayla birleştirilir.

### 3-Way Handshake (Üçlü El Sıkışma)

TCP, veri göndermeden önce iki taraf arasında bağlantı kurar:

```
Client                          Server
  |------ SYN ----------------->|   "bağlantı kurmak istiyorum"
  |<----- SYN-ACK --------------|   "tamam, ben de hazırım"
  |------ ACK ----------------->|   "harika, başlıyoruz"
```

Bu üç adım tamamlandıktan sonra bağlantı kurulur ve gerçek veri (HTTP isteği gibi) akmaya başlar.

**Neden bu el sıkışmaya gerek var?** İnternet güvenilmez bir ortamdır — paketler kaybolabilir, gecikebilir, bozulabilir. TCP, iki tarafın da "hazırım, konuşabiliriz" demesini garanti ederek sağlam bir temel kurar.

## 3. Gerçek Dünya Bağlantısı

Bir isteğe (`requests.get(...)`) çıkıldığında önce bu TCP el sıkışması gerçekleşir, **sonra** HTTP isteği bu bağlantı üzerinden gönderilir. HTTP, TCP'nin üzerine kurulu bir protokoldür — TCP taşımayı garanti eder, HTTP "ne taşındığını" tanımlar.

`uvicorn` ile FastAPI uygulaması çalıştırıldığında, uvicorn belirtilen portta TCP bağlantılarını dinlemeye başlar.

## Kritik Nokta — TCP vs UDP

TCP'nin alternatifi **UDP**'dir: el sıkışma yapmaz, paket kaybını garanti altına almaz — ama çok daha hızlıdır.

| Senaryo | Tercih | Neden |
|---|---|---|
| Dosya indirme (PDF vs.) | TCP | Tek bir bitin eksik olması dosyayı bozabilir; veri bütünlüğü kritik |
| Canlı video görüşmesi | UDP | Birkaç paket/frame kaybı küçük bir görsel bozulmaya yol açar ama **gecikme** çok daha rahatsız edicidir; anlık akış önceliklidir |

Web trafiğinde (HTTP/HTTPS) güvenilirlik öncelikli olduğu için TCP kullanılır.

## İlgili Notlar
- [[02-dns-ip-port|DNS, IP ve Port]]
- [[04-http-nedir|HTTP Nedir?]]
