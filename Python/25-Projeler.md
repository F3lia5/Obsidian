#python #proje-yonetimi #github

# Projeler

## Amaç
Öğrenilen her şeyi (OOP, dosya işlemleri, hata yönetimi, test yazma, venv) tek bir gerçek, katmanlı projede birleştirmek — GitHub'a koyulabilecek, "junior ödevi" değil "düzgün yapılandırılmış proje" izlenimi veren bir çalışma.

## Profesyonel Bir Projeyi Ayıran Şey

Sadece çalışan kod yeterli değil. Olması gerekenler:

```
proje_adi/
├── README.md              ← ne olduğunu, nasıl çalıştırılacağını anlatır
├── requirements.txt        ← bağımlılıklar
├── .gitignore                ← venv, __pycache__ hariç tutulur
├── src/ (ya da proje_adi/)    ← kod, TEK dosyada değil, mantıklı modüllere bölünmüş
│   ├── __init__.py
│   ├── models.py             ← sınıflar (OOP)
│   └── utils.py                ← yardımcı fonksiyonlar
└── tests/
    └── test_models.py
```

Kodu tek dosyada değil, **birden fazla dosyaya, mantıklı bir klasör yapısına** bölmek — Modüller dersindeki `import` mantığının gerçek hayattaki kullanımı.

## Mimari Prensip: Mantık ile Arayüz Ayrımı

Bir projeyi (örn. CLI'dan GUI'ye) değiştirirken, iş mantığı (models, storage, reports gibi) **değişmemeli** — sadece en dıştaki "kullanıcıyla konuşan" katman (argparse ↔ tkinter gibi) değişmeli.

```
proje/
├── src/
│   ├── models.py       ← DEĞİŞMEZ (iş mantığı)
│   ├── storage.py       ← DEĞİŞMEZ
│   ├── reports.py        ← DEĞİŞMEZ
│   └── gui.py / cli.py     ← arayüz katmanı, değişebilir
└── tests/                    ← iş mantığını test eder, arayüzü değil
```

## Değerlendirilen Proje Fikri: ExpenseTrack (Kişisel Harcama Takipçisi)

Şu ana kadarki tüm konuları anlamlı şekilde kullanan bir örnek:

| Konu | Nerede Kullanılır |
|---|---|
| OOP | `Harcama` sınıfı (tutar, kategori, tarih) |
| Enum | Kategori seçimi (yazım hatasını önler) |
| dataclass | `Harcama` sınıfını sadeleştirmek |
| Dosya + json | Harcamaları kalıcı saklamak |
| try/except | Geçersiz girdi koruması |
| List comprehension | Kategoriye göre filtreleme |
| datetime | Otomatik tarih damgası |
| Counter | En çok harcanan kategori |
| argparse (yeni, standart kütüphane) | `expensetrack ekle`, `expensetrack rapor` komutları |
| pytest | Model ve rapor fonksiyonlarını test etme |
| (opsiyonel) tkinter | CLI yerine pencereli arayüz |

**Not:** Standart kütüphane ağırlıklı tasarlarsan `requirements.txt` neredeyse boş kalabilir — dış bağımlılık olmadan da profesyonel bir proje çıkar.

## Özet
- Proje = README + requirements.txt + .gitignore + modüllere bölünmüş kod + tests/.
- İş mantığı ile arayüz katmanını ayırmak, projeyi CLI'dan GUI'ye (ya da web'e) geçirmeyi kolaylaştırır.
- Standart kütüphane (json, datetime, collections, argparse) çoğu zaman dış paket ihtiyacını ortadan kaldırır.
