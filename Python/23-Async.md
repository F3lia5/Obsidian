#python #async #ileri-seviye

# Asenkron Programlama (async/await)

## Amaç
I/O bekleyen işlemlerde (ağ isteği, dosya okuma, veritabanı) bekleme süresini "boşa harcamadan" başka işler yapabilmek.

## Senkron vs Asenkron

> **Senkron:** Tek garson, bir masaya sipariş alır, mutfağa gider, yemek pişene kadar **orada bekler**, sonra bir sonraki masaya gider.
>
> **Asenkron:** Aynı garson, siparişi mutfağa iletir, yemek pişerken **beklemez**, hemen başka masaya gider. Yemek hazır olunca götürür.

## `async def` ve `await`

```python
import asyncio

async def kahve_yap():
    print("Kahve hazırlanıyor...")
    await asyncio.sleep(3)   # 3 sn bekle ama BLOKE ETME
    print("Kahve hazır!")

asyncio.run(kahve_yap())
```

- `async def` → coroutine tanımlar
- `await` → "bekle ama bloklama, bu sırada başka işler yapılabilir"
- `time.sleep()` **programı tamamen durdurur**; `asyncio.sleep()` diğer coroutine'lerin çalışmasına izin verir

## `asyncio.gather()` — Birden Fazla İşi Eşzamanlı Yürütmek

```python
async def gorev(isim, sure):
    print(f"{isim} başladı")
    await asyncio.sleep(sure)
    print(f"{isim} bitti")

async def main():
    await asyncio.gather(
        gorev("Kahve", 3),
        gorev("Tost", 2),
        gorev("Çay", 1)
    )

asyncio.run(main())
```

**Senkron olsaydı:** 3+2+1 = 6 saniye (sırayla)
**Asenkron'da:** ~3 saniye (en uzun süren kadar, hepsi aynı anda başlar)

## Ne Zaman Kullanılır?
- **I/O-bound** işlerde (ağ isteği, dosya, veritabanı) faydalı
- **CPU-bound** (yoğun hesaplama) işlerde fayda sağlamaz — bekleme yok ki optimize edilsin

## Yaygın Hatalar
- `async def` içinde `await` kullanmayı unutmak
- `await`'i `async def` olmayan bir fonksiyonda kullanmak → `SyntaxError`
- `asyncio.sleep()` yerine `time.sleep()` kullanmak → tüm programı bloke eder
- CPU-yoğun işlerde async'ten hız beklemek

## Özet
- Senkron kod sırayla bekler, asenkron kod bekleme süresini boşa harcamaz.
- `async def` + `await` = coroutine tanımlama ve bekleme.
- `asyncio.gather()` = birden fazla coroutine'i eşzamanlı çalıştırma.
- I/O-bound işlerde faydalı, CPU-bound işlerde değil.

## Kişisel Not
Bu konuyu ileride gerçek bir projede (API isteği gibi somut bir senaryoda) pratiğe dökmek daha mantıklı — soyut örnekle teoriyi anlamak yeterliydi.
