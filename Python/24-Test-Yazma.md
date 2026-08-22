#python #pytest #test #proje-yonetimi

# Test Yazma (unittest, pytest)

## Amaç
Kodun doğru çalıştığını **otomatik ve tekrarlanabilir** şekilde doğrulamak. GitHub'daki ciddi projelerde neredeyse her zaman bir `tests/` klasörü vardır.

## Neden Test Yazarız?
Bir fonksiyonu değiştirdiğinde (optimize ettiğinde), hâlâ doğru çalıştığından emin olman gerekir. Elle her seferinde test etmek yerine, testi bir kere yazıp **otomatikleştirirsin**.

## Kurulum

```bash
pip install pytest
```

## Basit Bir Test

```python
# hesap.py
def topla(a, b):
    return a + b
```

```python
# test_hesap.py  (dosya adı test_ ile başlamalı!)
from hesap import topla

def test_topla():
    assert topla(2, 3) == 5
    assert topla(-1, 1) == 0
    assert topla(0, 0) == 0
```

**`assert`** = "bunun doğru olduğunu iddia ediyorum". Doğruysa hiçbir şey olmaz (test geçer), yanlışsa `AssertionError` (test başarısız).

Çalıştırma:
```bash
pytest test_hesap.py -v
```

## İsimlendirme Kuralları
- Dosya adı: `test_*.py` ya da `*_test.py`
- Fonksiyon adı: `test_` ile başlamalı
- pytest bu kurala uyanları **otomatik bulur**

## Hata Durumlarını Test Etmek

```python
import pytest

def bol(a, b):
    if b == 0:
        raise ValueError("Sıfıra bölünemez")
    return a / b

def test_bol_sifir():
    with pytest.raises(ValueError):
        bol(10, 0)
```

## Birden Fazla Senaryo — `@pytest.mark.parametrize`

```python
@pytest.mark.parametrize("a, b, beklenen", [
    (2, 3, 5),
    (-1, 1, 0),
    (0, 0, 0),
])
def test_topla_coklu(a, b, beklenen):
    assert topla(a, b) == beklenen
```

## Yaygın Hatalar
- Test dosyasını `test_` ile başlatmamak → pytest bulamaz
- Sadece "mutlu senaryoları" test etmek → **edge case**'ler (boş liste, negatif sayı, sıfıra bölme) en değerli testlerdir
- Testin kendisinde mantık hatası olması

## Best Practice
Her fonksiyon için en az: (1) normal durum, (2) sınır durumu (edge case), (3) mümkünse hata durumu test et. Test isimleri açıklayıcı olmalı (`test_topla_negatif_sayilar` gibi).

## Kişisel Not — Örnek Test Dosyası
```python
class Ogrenci:
    def __init__(self, isim, notlar):
        self.isim = isim
        self.notlar = notlar

    def ortalama_hesapla(self):
        return sum(self.notlar) // len(self.notlar)

def test_ogrenci_olusturma():
    ogrenci = Ogrenci("Ali", [80, 90, 100])
    assert ogrenci.isim == "Ali"
    assert ogrenci.notlar == [80, 90, 100]

def test_ortalama_hesapla():
    ogrenci = Ogrenci("Ayse", [60, 80, 100])
    assert ogrenci.ortalama_hesapla() == 80

def test_kusuratli_ortalama():
    # // kullandığımız için sonuç tamsayı olmalı (250 // 3 = 83)
    ogrenci = Ogrenci("Mehmet", [80, 85, 85])
    assert ogrenci.ortalama_hesapla() == 83
```
Çalıştırınca: `3 passed` ✅ — en değerli test, kusuratlı bölme (`//`) davranışını doğrulayan `test_kusuratli_ortalama` idi, çünkü sadece "beklenen" senaryoyu değil, ilginç bir edge case'i (küsüratın atılması) kontrol ediyor.

## Özet
- `pytest` = fonksiyonların doğruluğunu otomatik doğrulama aracı.
- `assert` = iddia; yanlışsa `AssertionError`.
- `pytest.raises()` = hata fırlatmayı test etme.
- `@pytest.mark.parametrize` = çoklu senaryoyu tek fonksiyonda test etme.
