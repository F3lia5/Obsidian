#python #kariyer #uzmanlik

# Uzmanlaşma Alanları

## Amaç
Python bir araçtır, kendisi bir kariyer hedefi değil. Bu ders, hangi yönde derinleşilebileceğini özetler.

## Başlıca Alanlar

### Web Backend Geliştirme
- **Django** → büyük, "her şey dahil" framework (admin panel, ORM, kullanıcı sistemi hazır). Kurumsal projelerde yaygın.
- **FastAPI** → modern, hızlı, async ağırlıklı, API yazmaya odaklı. Son yıllarda popüler.
- **Flask** → minimal, esnek, küçük projeler için.
- *Kimin için:* Web siteleri, mobil uygulama API'leri, SaaS ürünleri.

### Veri Bilimi / Makine Öğrenmesi
- **pandas** → tablo/Excel benzeri veri işleme
- **numpy** → sayısal/matematiksel işlemler, matrisler
- **matplotlib / seaborn** → veri görselleştirme
- **scikit-learn** → klasik makine öğrenmesi
- **PyTorch / TensorFlow** → derin öğrenme (ileri seviye)
- *Kimin için:* Matematik/istatistiğe ilgisi olan, veriden içgörü çıkarmak isteyenler.

### Otomasyon / Scripting
- Dosya organizasyonu, web scraping (`BeautifulSoup`, `Selenium`), Excel otomasyonu (`openpyxl`), sistem yönetimi scriptleri
- *Kimin için:* IT/sistem yöneticiliği, günlük iş süreçlerini hızlandırmak isteyenler.

### Oyun Geliştirme
- **Pygame** → 2D oyunlar, öğretici
- Büyük ölçekli oyunlar genelde C++/Unity kullanır; Python öğrenme/prototipleme için değerli.

### Siber Güvenlik / Pentest
- Port tarayıcılar, ağ analizi, güvenlik testleri
- **Scapy** (ağ paketi analizi), **requests** (web güvenlik testleri)

### DevOps / Altyapı
- Sunucu yönetimi, CI/CD, container otomasyonu
- **Ansible**, **Docker SDK for Python**

## Yapay Zeka ve Python

Python, YZ alanının fiili standart dili — ama Python'ın kendisi yavaş, asıl ağır hesaplamalar arka planda **C/C++ ve CUDA (GPU)** ile yapılır. Python burada kolay okunabilir bir arayüz görevi görür.

**Katmanlar:**
1. **Veri Hazırlama** → `pandas`, `numpy`
2. **Model Kurma/Eğitme** → `PyTorch` (Meta), `TensorFlow` (Google) — derin öğrenme
3. **Eğitim Süreci** → model tahmin yapar → hatayı hesaplar → parametreleri ayarlar → milyonlarca kez tekrarlar (döngü mantığının kozmik ölçekte hali)
4. **Kullanım (Inference)** → eğitilmiş modeli basit bir Python scriptiyle çağırmak (`model.predict(veri)`)

**Var olan bir modeli API üzerinden kullanmak** (model eğitmek değil) aslında öğrenilen konularla çok yakın:
- `requests` ile API'ye istek atmak
- `json` ile cevabı işlemek
- `try/except` ile hata yönetimi
- `async` ile birden fazla isteği eşzamanlı yapmak

## Projeyi Nasıl Sunarsın? (Terminal mi, Pencere mi, Web mi?)

| Yöntem | Araç | Ne Zaman |
|---|---|---|
| Terminal/CLI | `argparse`, `input()`/`print()` | Basit, teknik kullanıcılar için |
| Masaüstü (GUI) | `Tkinter` (yerleşik), `PyQt`/`PySide` (profesyonel) | Tıklanabilir arayüz isteyenler |
| Web Uygulaması | `Flask`/`Django`/`FastAPI` + HTML/CSS/JS | Tarayıcıdan erişim |
| Mobil | `Kivy` (az yaygın, genelde Kotlin/Swift/Flutter tercih edilir) | Mobil uygulama |
| API / Arka plan servisi | Framework + sunucu | Kullanıcı arayüz görmez, başka sistemlere hizmet eder |

**Önemli mimari prensip:** İş mantığı (business logic) ile arayüz birbirinden bağımsız tutulmalı — aynı `models.py`/`storage.py` kodu, ister CLI ister GUI ister web ile kullanılabilir, sadece en dıştaki katman değişir.

## Özet
- Python tek başına hedef değil, yön belirlemek gerekiyor: backend, veri bilimi, otomasyon, oyun, güvenlik, DevOps.
- YZ alanında Python arayüz katmanıdır, ağır iş C/C++/CUDA'da yapılır — ama API üzerinden model kullanmak öğrenilen temel becerilerle (requests, json, async) doğrudan ilişkilidir.
- Proje sunumu (terminal/GUI/web) tercih meselesidir, iş mantığı bundan bağımsız tutulmalı.

---

## 🎓 Kurs Özeti (Genel)

**Temel yapı taşları:** sözdizimi, operatörler, koşullar, döngüler, veri tipleri (string, liste, tuple, set, dictionary)
**Fonksiyonel düşünme:** fonksiyonlar, scope, modüller, list comprehension, generator, decorator
**OOP:** sınıflar, nesneler, magic method'lar, dataclass, enum
**Gerçek dünya becerileri:** dosya işlemleri, hata yönetimi, standart kütüphaneler, venv, async, test yazma
