#python #temel #kurulum

# 🗺️ Bu Dilde Öğreneceklerin

Bu kurs, Python'ı sıfırdan ileri seviyeye taşıyan 26 dersten oluşuyor. Temelde [[02-Temel-Sozdizimi]], [[03-Operatorler]], [[04-Kosullar]] ve [[05-Donguler]] ile programın "dilbilgisini" öğreneceksin. Ardından [[06-Stringler]], [[07-Listeler]], [[08-Tuple]], [[09-Set]] ve [[10-Dictionary]] ile Python'ın veri tiplerini keşfedeceksin. [[11-Fonksiyonlar]], [[12-Scope]] ve [[13-Moduller]] ile kodu tekrar kullanılabilir, düzenli parçalara ayırmayı; [[14-Dosya-Islemleri]] ve [[15-Hata-Yonetimi]] ile kalıcı ve dayanıklı programlar yazmayı öğreneceksin. [[16-List-Comprehension]], [[17-Generator]] ve [[18-Decorator]] seni daha "Pythonic" ve ileri seviye bir yazım tarzına taşıyacak; bunun üzerine [[19-OOP]] ve [[20-Ileri-Python]] ile nesne yönelimli programlamanın temellerini kuracaksın. [[21-Standart-Kutuphaneler]], [[22-Virtual-Environment]] ve [[23-Async]] ile gerçek dünya araçlarını, [[24-Test-Yazma]] ile kodunun doğruluğunu kanıtlamayı öğreneceksin. Son olarak [[25-Projeler]] ile öğrendiğin her şeyi tek bir çalışmada birleştirecek, [[26-Uzmanlasma-Alanlari]] ile bu bilgiyi nereye yönlendirebileceğini göreceksin.

## Amaç
Çalışma ortamını doğru kurmak — yanlış sürüm, PATH sorunları gibi başlangıç engellerini aşmak.

## Teori
Python **yorumlanan (interpreted)** bir dildir. CPython (referans implementasyon), kodu satır satır okuyup **bytecode**'a çevirir, bu bytecode Python Virtual Machine (PVM) üzerinde çalışır.

**Akış:** Kaynak kod (.py) → Bytecode → Python Virtual Machine → Sonuç

### Kurulum İçin Gereken 3 Bileşen
1. **Python Yorumlayıcısı** — python.org'dan veya paket yöneticisinden (Arch'ta `pacman`)
2. **pip** — Python paket yöneticisi
3. **Bir kod editörü/IDE** — VS Code, PyCharm, nvim (kişiselleştirilmiş)

### Neden Python 3?
Python 2, 2020'de resmen **EOL (End of Life)** oldu — güvenlik yaması/hata düzeltmesi almıyor. Ayrıca Python 3'te dil düzeyinde iyileştirmeler var (string'lerin varsayılan Unicode olması, `print`'in fonksiyon olması vs.).

## Temel Komutlar

```bash
python --version      # sürüm kontrolü
which python           # hangi python çalıştığını gösterir
pip --version           # pip sürümü
python                    # REPL'i açar
```

## REPL vs .py Dosyası — Kritik Fark

```python
>>> print("Felias")
Felias
>>> "Felias"
'Felias'
```

- `print()` → string'in **okunabilir** (`str()`) halini basar, tırnaksız.
- REPL'in otomatik gösterdiği değer → `repr()` halidir, tırnaklıdır ("bu bir string" bilgisini de verir).
- **REPL, `print` kullanmasan bile ifadenin sonucunu otomatik gösterir.** `.py` dosyasında bu olmaz — orada mutlaka `print()` yazman gerekir.

## CPython vs PyPy (İleri Bilgi)

- **CPython:** Kodu her çalıştırdığında satırları yeniden yorumlar, optimizasyon yapmaz.
- **PyPy:** JIT (Just-In-Time) derleme yapar — sık çalışan kod bloklarını makine koduna derler, sonraki çalıştırmalarda hızlıdır.
- CPython hâlâ endüstri standardı çünkü C-extension kütüphaneleriyle (NumPy gibi) en uyumlu olan implementasyon.

## Yaygın Hatalar
- `python` yerine sistemde Python 2'nin çağrılması (bazı sistemlerde) — `python3` kullanmak daha güvenli (Arch'ta genelde `python` zaten Python 3'e işaret eder)
- pip'i güncellememek
- Sanal ortam kullanmadan direkt global kuruluma paket yüklemek
- IDE'yi Python yorumlayıcısına tanıtmayı unutmak

## Özet
- Python yorumlanan bir dil, CPython bytecode'a çevirip PVM'de çalıştırır.
- Kurulum: Python + pip + IDE.
- REPL, `print` olmasa bile ifadenin `repr()` halini otomatik gösterir; `.py` dosyasında bu olmaz.
- CPython = referans implementasyon; PyPy = JIT ile hızlandırılmış alternatif.
