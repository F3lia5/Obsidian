#python #scope #fonksiyonlar

# Scope (Local / Global)

## Amaç
Fonksiyonlar dersinde görülen "fonksiyon içindeki değişkene dışarıdan erişilemiyor" durumunun **neden** olduğunu netleştirmek. Anlaşılmazsa fonksiyonlarda açıklanamayan hatalara yol açar.

## Local Scope (Yerel Kapsam)

Bir fonksiyon içinde tanımlanan değişkenler sadece o fonksiyonun içinde yaşar, fonksiyon bitince yok olur.

```python
def fonksiyon():
    x = 10   # x, LOCAL bir değişken
    print(x)

fonksiyon()
print(x)     # NameError! x fonksiyon dışında tanımlı değil
```

## Global Scope (Genel Kapsam)

Fonksiyonların dışında, en üst seviyede tanımlanan değişkenler globaldir — her yerden **okunabilir**.

```python
y = 100    # GLOBAL değişken

def fonksiyon():
    print(y)    # ✅ çalışır, global değişkeni OKUYABİLİRSİN

fonksiyon()
```

## Kritik Tuzak: Global Değişkeni Fonksiyon İçinde Değiştirmek

```python
sayac = 0

def arttir():
    sayac = sayac + 1   # UnboundLocalError!
```

**Neden hata verir?** Python, bir fonksiyon içinde bir değişkene **herhangi bir yerde atama** yapıldığını görürse, o değişkeni **baştan itibaren local** sayar — fonksiyonun neresinde olursa olsun. `sayac = sayac + 1` satırındaki sağdaki `sayac`'ı okumaya çalıştığında, Python onu "local sayac" olarak arar ama henüz atanmadığı için bulamaz.

### Çözüm 1 — `global` anahtar kelimesi

```python
sayac = 0

def arttir():
    global sayac      # "bu fonksiyonda sayac derken GLOBAL olanı kastediyorum"
    sayac = sayac + 1

arttir()
print(sayac)   # 1
```

### Çözüm 2 — `return` (Tercih Edilen Yöntem)

`global` teknik olarak çalışır ama gerçek projelerde **kaçınılması önerilir** çünkü fonksiyonun dışarıdaki bir şeyi "gizlice" değiştirmesine izin verir — kodun takibini zorlaştırır.

```python
sayac = 0

def arttir(mevcut_sayac):
    return mevcut_sayac + 1

sayac = arttir(sayac)   # daha temiz, açık, takip edilebilir
```

## Görsel Mantık

```
GLOBAL SCOPE (dış dünya)
┌─────────────────────────────────┐
│  y = 100                          │
│                                    │
│   LOCAL SCOPE (fonksiyon içi)     │
│   ┌───────────────────────┐       │
│   │  def fonksiyon():     │       │
│   │      x = 10            │       │
│   │      print(y)  ← okuma OK    │
│   └───────────────────────┘       │
│                                    │
│  print(x)  ← ERROR, x burada yok │
└─────────────────────────────────┘
```

> Tek yönlü cam gibi düşün: içeriden dışarı bakabilirsin (okuma), ama dışarıdan içeri göremezsin.

## Yaygın Hatalar
- Fonksiyon içinde tanımlanan değişkene dışarıdan erişmeye çalışmak → `NameError`
- Global değişkeni `global` demeden fonksiyon içinde güncellemeye çalışmak → `UnboundLocalError`
- Gereksiz yere her yerde `global` kullanmak → kod karmaşıklaşır, hangi fonksiyonun neyi değiştirdiği takip edilemez hale gelir

## Kişisel Not — `return` ile "Hesaplama" vs "Kalıcı Güncelleme" Farkı
```python
bakiye = 1000

def para_cek(miktar):
    return bakiye - miktar   # sadece OKUMA yapıyor, atama yok, hata vermiyor

print(para_cek(200))   # 800 yazar (anlık hesaplama)
print(bakiye)            # hâlâ 1000! çünkü bakiye'ye hiç atama yapılmadı
```
`return` bir değer üretir ama o değeri bir değişkene **atamazsan**, orijinal değişken değişmeden kalır. Kalıcı güncelleme için dönen değeri geri atamak gerekir:
```python
bakiye = para_cek(bakiye, miktar)   # sayac = arttir(sayac) ile aynı kalıp
```

## Özet
- Local değişkenler sadece tanımlandıkları fonksiyon içinde yaşar.
- Global değişkenler her yerden okunabilir ama fonksiyon içinde değiştirmek için `global` gerekir.
- Bir değişkene fonksiyon içinde atama yapılırsa Python onu local sayar (`UnboundLocalError` riski); sadece okuma yapılırsa sorun çıkmaz.
- `global` yerine parametre + `return` + geri atama kalıbı daha temiz ve tercih edilen yöntemdir.
