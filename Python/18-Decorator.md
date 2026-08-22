#python #decorator #ileri-seviye

# Decorator

## Amaç
Bir fonksiyonun davranışını, **fonksiyonun kodunu değiştirmeden** genişletmek. Flask, Django, pytest gibi araçlarda her yerde karşına çıkar.

## Ön Koşul: Fonksiyonlar da Birer "Değer"dir

```python
def selamla():
    print("Merhaba")

x = selamla   # parantez YOK, fonksiyonun kendisini x'e atadık
x()           # şimdi çağırabiliriz
```

`selamla` (parantezsiz) → fonksiyonun **kendisi**
`selamla()` → fonksiyonu **çağırmak**

## Temel Yapı

```python
def decorator(fonksiyon):
    def wrapper():
        print("ÖNCE")
        fonksiyon()
        print("SONRA")
    return wrapper

def selamla():
    print("Merhaba!")

selamla = decorator(selamla)   # selamla'yı sarmalıyoruz
selamla()
```

**Kritik nokta:** `decorator` fonksiyonu, asıl fonksiyonu **hemen çağırmaz** — içeride bir `wrapper` tanımlar ve onu `return` eder. Asıl çalışma, `wrapper` çağrıldığında olur.

## `@` Sözdizimi (Syntactic Sugar)

```python
@decorator
def selamla():
    print("Merhaba!")

selamla()   # ÖNCE / Merhaba! / SONRA
```

`@decorator` = `selamla = decorator(selamla)` satırının kısa hali.

## Parametreli Fonksiyonları Decorate Etmek

```python
def decorator(fonksiyon):
    def wrapper(*args, **kwargs):
        print("ÖNCE")
        sonuc = fonksiyon(*args, **kwargs)
        print("SONRA")
        return sonuc
    return wrapper

@decorator
def topla(a, b):
    return a + b

print(topla(3, 5))
```

`*args, **kwargs` → wrapper'ın her türlü parametreyi kabul etmesini sağlar.

## Yaygın Hatalar
- `wrapper`'ın `return` etmeyi unutması → asıl fonksiyonun sonucu kaybolur (`None` döner)
- `wrapper(*args, **kwargs)` yazmayı unutmak → parametreli fonksiyonlarda `TypeError`
- Decorator'ın "tanımlanır tanımlanmaz bir kere sarma yaptığını", asıl kodun "her çağrıldığında" çalıştığını karıştırmak

## Kişisel Not (kendi hatamdan öğrendiğim)
`fonkyon` yazmak onu **çağırmak değildir** — sadece referans. Çalıştırmak için `fonkyon(a, b)` gerekir. Ayrıca `wrapper` içinde asıl fonksiyonun sonucunu bir değişkende yakalayıp (`sonuc = fonkyon(a,b)`) sonra `return sonuc` yapmazsam, dışarıya `None` sızar — iki farklı `return` (biri asıl fonksiyonda, biri wrapper'da) zincirinin ikisi de gerekli.

## Özet
- Fonksiyonlar Python'da birer değerdir.
- Decorator = fonksiyonu sarmalayan bir fonksiyon, `@` ile kısaca uygulanır.
- `wrapper`'ın parametre alması ve `return` etmesi kritik.
