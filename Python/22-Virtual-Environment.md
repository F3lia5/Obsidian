#python #venv #proje-yonetimi

# Virtual Environment (venv)

## Amaç
Her proje için izole, bağımsız bir Python ortamı — versiyon çakışmalarını önler. GitHub'a koyulacak her proje için zorunlu bilgi.

## Sorun Neydi?
Sistem genelinde (global) paket kurarsan: Proje A `requests==2.0` ister, Proje B `requests==3.0` ister → biri diğerini ezer.

> Benzetme: Ortak mutfak yerine, her dairenin kendi bağımsız mutfağı.

## Oluşturma ve Aktifleştirme

```bash
python -m venv venv_adi          # sanal ortam oluştur
source venv_adi/bin/activate      # aktifleştir (Linux/Mac)
deactivate                          # çıkış
```

Aktifken terminalde `(venv_adi)` öneki görünür. Bu haldeyken `pip install` yapılan her şey **sadece bu projeye** özel kalır.

## `requirements.txt` — Bağımlılıkları Kaydetmek

```bash
pip freeze > requirements.txt      # kurulu paketleri dosyaya dök
pip install -r requirements.txt     # başka biri aynı ortamı tek komutla kurar
```

## `.gitignore` ile venv'i Git'e Eklememe

**KRİTİK:** `venv/` klasörü asla GitHub'a yüklenmez (çok büyük + gereksiz, herkes kendi venv'ini kurar).

```
venv/
__pycache__/
*.pyc
```

## Kalıcılık Notu
`venv` klasörü diskte fiziksel olarak durur — terminali kapatmak kurulan kütüphaneleri silmez. Her yeni terminal oturumunda sadece `source venv/bin/activate` tekrar çalıştırılmalı.

## Yaygın Hatalar
- venv aktifleştirmeden `pip install` yapmak → global'e kurulur, çakışma riski
- `venv/` klasörünü Git'e yüklemek
- `requirements.txt` oluşturmayı unutmak

## Özet
- `python -m venv venv` → oluştur, `source venv/bin/activate` → gir, `deactivate` → çık.
- `pip freeze > requirements.txt` → bağımlılıkları kaydet.
- `venv/` her zaman `.gitignore`'da olmalı.
