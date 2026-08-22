# 💰 ExpenseTrack (Kişisel Harcama Takipçisi) - Proje Planı

> **Amaç:** Python standart kütüphanelerini, OOP ilkelerini ve katmanlı mimariyi (Business Logic ile GUI ayrımı) pekiştiren, Tkinter tabanlı masaüstü harcama takip uygulaması geliştirmek.

---

## 🛠️ Hazırlık ve Kurulum

- [x] **Sistem Bağımlılıkları:**
  - [x] Tkinter kütüphanesinin kurulu olduğunu kontrol et (Arch Linux için: `sudo pacman -S tk`)
- [x] **Proje Dizin Yapısını Oluştur:**
  ```text
  expensetrack/
  ├── README.md
  ├── requirements.txt
  ├── .gitignore
  ├── src/
  │   ├── models.py
  │   ├── storage.py
  │   ├── reports.py
  │   └── gui.py
  ├── tests/
  │   └── test_models.py
  └── expensetrack.py
  ```
- [x] Bir sanal ortam (venv) ve `pytest` kurulumu yap (testler için).

---

## 📦 Katman 1: Veri Modelleri (`src/models.py`)

- [x] `Enum` kullanarak **Kategori** sınıfını tanımla (ör. `Yiyecek`, `Ulasim`, `Eglence`, `Diger`).
- [ ] `@dataclass` kullanarak **Harcama** (`Expense`) sınıfını oluştur:
  - [x] Nitelikler: `tutar` (float/int), `kategori` (Enum/str), `notlar` (str), `tarih` (datetime ISO string).
%%  - [ ] Hatalı tutar veya eksik alan girildiğinde `try/except` ile yakalanabilecek veri doğrulama (validation) ekle. (tk dene ise yaramazsa gel yap)%%
  

---

## 💾 Katman 2: Veri Saklama ve Dosya İşlemleri (`src/storage.py`)

- [x] `harcamalar.json` dosyasından veri okuyan ve yazan fonksiyonları yaz.
- [x] `try/except` yapısı ile dosya bulunamadığında (`FileNotFoundError`) ya da JSON bozuk olduğunda uygulamanın çökmesini engelle.
- [x] Nesneleri JSON uyumlu `dict` yapılarına (ve tersine) dönüştüren serializer/deserializer yardımcılarını yaz.

---

## 📊 Katman 3: Raporlama Mantığı (`src/reports.py`)

- [ ] List comprehension kullanarak kategoriye/tarihe göre harcama filtreleme fonksiyonları yaz.
- [ ] Toplam harcamayı hesaplayan fonksiyonu yaz.
- [ ] `collections.Counter` kullanarak en çok harcama yapılan kategoriyi tespit et.
- [ ] Aylık/kategorik bazda özet rapor nesnesi/metni oluşturan mantığı kur.

---

## 🖥️ Katman 4: Kullanıcı Arayüzü (`src/gui.py`)

- [ ] Tkinter ana penceresini (`Tk()`) oluştur ve başlık/boyut ayarlarını yap.
- [ ] **Girdi Alanları (Entry/OptionMenu):**
  - [ ] Tutar girişi için `Entry`
  - [ ] Kategori seçimi için `OptionMenu` / `Combobox` (Enum bazlı)
  - [ ] Açıklama/Not için `Entry`
- [ ] **Ekle Butonu:**
  - [ ] Tıklanınca girdileri alan, doğrulayan, `models` üzerinden nesne yapıp `storage` ile kaydeden callback fonksiyonunu bağla.
- [ ] **Görselleştirme/Listeleme Alanı:**
  - [ ] Eklenen harcamaları listeleyen bir tablo/liste widget'ı (ör. `Treeview` veya `Listbox`).
- [ ] **Rapor / Özet Alanı:**
  - [ ] Toplam harcama ve en çok harcanan kategori özetini gösteren metin alanı (`Label`/`Text`).

---

## 🚀 Katman 5: Ana Giriş Noktası (`expensetrack.py`)

- [ ] `gui.py` içindeki ana arayüz döngüsünü (`mainloop()`) başlatan giriş kodunu yaz.

---

## 🧪 Katman 6: Test ve Kalite (`tests/test_models.py`)

- [ ] `pytest` ile `models.py` içindeki doğrulama ve nesne oluşturma mantığını test et.
- [ ] `storage.py` ve `reports.py` fonksiyonları için birim (unit) testleri yaz.
- [ ] Arayüzden bağımsız olarak arka plan mantığının (business logic) çalıştığından emin ol.

---

## 📝 Dokümantasyon ve GitHub Hazırlığı

- [ ] Uygulama ekran görüntüsünü veya demo GIF'ini `README.md` dosyasına ekle.
- [ ] `README.md` içine çalıştırma talimatlarını yaz.
- [ ] Gereksiz dosyaları `.gitignore` içine ekle.
