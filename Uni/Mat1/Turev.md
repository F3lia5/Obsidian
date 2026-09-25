# Türev

> [!abstract] Konu
> Bir fonksiyonun **anlık değişim hızını** ve grafiğinin bir noktadaki **teğet eğimini** inceleyen matematiksel araç.
>
> **Seviye:** 12. sınıf sonu → Üniversite 1

---

## 1. Türev Neyi Ölçer?

Türevin temel fikri şudur:

> **Bir şey ne kadar hızlı değişiyor?**

Örneğin bir arabanın konumunu zamana bağlı olarak

$$
s(t)
$$

ile gösterelim.

Ortalama hız:

$$
\frac{\Delta s}{\Delta t}
$$

şeklindedir.

Ancak bu bize belirli bir zaman aralığındaki ortalama hızı verir.

Örneğin:

> Araba 0–10 saniye arasında ortalama 20 m/s hızla gitmiş.

Ama **tam olarak 5. saniyedeki hızı** nedir?

Burada türev devreye girer.

$$
v(t)=s'(t)
$$

Yani konumun zamana göre türevi bize **anlık hızı** verir.

### Temel fikir

$$
\boxed{\text{Türev = Anlık değişim hızı}}
$$

Geometrik olarak:

$$
\boxed{\text{Türev = Bir noktadaki teğet doğrusunun eğimi}}
$$

---

# 2. Ortalama Değişim Oranı

Bir fonksiyonun \(x=a\) ile \(x=b\) arasındaki ortalama değişim oranı:

$$
\frac{f(b)-f(a)}{b-a}
$$

şeklindedir.

Bu ifade aynı zamanda grafikte:

> \(x=a\) ve \(x=b\) noktalarından geçen doğrunun eğimidir.

Bu doğruya **sekant doğrusu** denir.

Örneğin:

$$
f(x)=x^2
$$

için \(x=1\) ve \(x=3\) arasındaki ortalama değişim oranı:

$$
\frac{f(3)-f(1)}{3-1}
=
\frac{9-1}{2}
=
4
$$

Yani bu aralıktaki ortalama eğim 4'tür.

---

# 3. Anlık Değişim Oranı

Şimdi iki noktanın birbirine giderek yaklaştığını düşünelim.

İkinci noktayı:

$$
a+h
$$

olarak yazalım.

Bu durumda iki nokta arasındaki eğim:

$$
\frac{f(a+h)-f(a)}{h}
$$

olur.

Burada \(h\), iki \(x\) değeri arasındaki uzaklıktır.

Şimdi:

$$
h\rightarrow0
$$

yani ikinci noktayı birinci noktaya sonsuz derecede yaklaştırırsak sekant doğrusu **teğet doğrusuna yaklaşır.**

Dolayısıyla türevin temel tanımı:

$$
\boxed{
f'(a)=
\lim_{h\to0}
\frac{f(a+h)-f(a)}{h}
}
$$

Bu ifadeye **fark bölümü** denir.

---

# 4. Türev Tanımı

Bir fonksiyonun \(x\) noktasındaki türevi:

$$
\boxed{
f'(x)=
\lim_{h\to0}
\frac{f(x+h)-f(x)}{h}
}
$$

şeklindedir.

Türev için farklı gösterimler kullanılabilir:

$$
f'(x)
$$

$$
\frac{dy}{dx}
$$

$$
y'
$$

$$
D_xf(x)
$$

Hepsi bağlama göre aynı türev kavramını ifade eder.

---

# 5. Türevin Geometrik Anlamı

Bir fonksiyonun grafiğinde:

$$
y=f(x)
$$

olsun.

\(x=a\) noktasındaki türev:

$$
f'(a)
$$

grafiğin o noktadaki **teğet doğrusunun eğimidir.**

### İşaret ne anlatır?

Eğer:

$$
f'(a)>0
$$

ise grafik o noktada genel olarak **yükseliyor**.

Eğer:

$$
f'(a)<0
$$

ise grafik o noktada genel olarak **azalıyor**.

Eğer:

$$
f'(a)=0
$$

ise teğet yataydır.

Bu durum özellikle **maksimum ve minimum** problemlerinde önemlidir.

---

# 6. Türev Tanımından Türev Alma

Örneğin:

$$
f(x)=x^2
$$

olsun.

Tanımdan başlayalım:

$$
f'(x)
=
\lim_{h\to0}
\frac{f(x+h)-f(x)}{h}
$$

Fonksiyonda \(x\) yerine \(x+h\) yazarsak:

$$
f(x+h)=(x+h)^2
$$

Dolayısıyla:

$$
f'(x)
=
\lim_{h\to0}
\frac{(x+h)^2-x^2}{h}
$$

Açalım:

$$
=
\lim_{h\to0}
\frac{x^2+2xh+h^2-x^2}{h}
$$

$$
=
\lim_{h\to0}
\frac{2xh+h^2}{h}
$$

$$
=
\lim_{h\to0}(2x+h)
$$

$$
\boxed{f'(x)=2x}
$$

Buradaki önemli nokta:

> Türev tanımında doğrudan \(h=0\) yazılmaz. Önce sadeleştirme yapılır, ardından limit alınır.

---

# 7. Temel Türev Kuralları

Türev tanımını her seferinde kullanmak çok zahmetlidir.

Bu yüzden sık kullanılan fonksiyonların türevlerini ve türev kurallarını kullanırız.

---

## 7.1 Sabitin Türevi

$$
f(x)=c
$$

ise:

$$
\boxed{f'(x)=0}
$$

Örneğin:

$$
f(x)=7
$$

$$
f'(x)=0
$$

Çünkü sabit bir şey değişmez.

---

## 7.2 Kuvvet Kuralı

En önemli kurallardan biri:

$$
\boxed{
\frac{d}{dx}x^n=nx^{n-1}
}
$$

Örneğin:

$$
f(x)=x^5
$$

ise:

$$
f'(x)=5x^4
$$

### Katsayı varsa

$$
f(x)=3x^4
$$

$$
f'(x)=12x^3
$$

Çünkü:

$$
3\cdot4x^3=12x^3
$$

### Genel biçim

$$
f(x)=ax^n
$$

ise:

$$
\boxed{
f'(x)=anx^{n-1}
}
$$

---

# 8. Toplam ve Farkın Türevi

Fonksiyonların toplamının türevi:

$$
\boxed{
(f+g)'=f'+g'
}
$$

Fark için:

$$
\boxed{
(f-g)'=f'-g'
}
$$

Örneğin:

$$
f(x)=x^4+3x^2-5x+7
$$

ise:

$$
f'(x)=4x^3+6x-5
$$

Sabit olan \(7\)'nin türevi 0 olduğu için yazılmaz.

---

# 9. Sabit Katsayı Kuralı

$$
\boxed{
(cf)'=cf'
}
$$

Örneğin:

$$
f(x)=7x^3
$$

$$
f'(x)=7(3x^2)
$$

$$
\boxed{f'(x)=21x^2}
$$

---

# 10. Çarpım Kuralı

İki fonksiyon çarpılıyorsa:

$$
f(x)=u(x)v(x)
$$

türev:

$$
\boxed{
(uv)'=u'v+uv'
}
$$

Yani:

> **Birincinin türevi × ikinci + birinci × ikincinin türevi**

Örneğin:

$$
f(x)=x^2\sin x
$$

olsun.

$$
u=x^2
$$

$$
v=\sin x
$$

$$
u'=2x
$$

$$
v'=\cos x
$$

Dolayısıyla:

$$
f'(x)
=
2x\sin x+x^2\cos x
$$

### Önemli

$$
(uv)' \neq u'v'
$$

Çarpımın türevi **iki terimlidir.**

---

# 11. Bölüm Kuralı

İki fonksiyon bölünüyorsa:

$$
f(x)=\frac{u(x)}{v(x)}
$$

türevi:

$$
\boxed{
\left(\frac{u}{v}\right)'
=
\frac{u'v-uv'}{v^2}
}
$$

Ezberlemek için:

> **Üstün türevi × alt − üst × altın türevi / altın karesi**

Örneğin:

$$
f(x)=\frac{x^2}{x+1}
$$

için:

$$
u=x^2,\quad u'=2x
$$

$$
v=x+1,\quad v'=1
$$

Dolayısıyla:

$$
f'(x)
=
\frac{2x(x+1)-x^2}{(x+1)^2}
$$

---

# 12. Zincir Kuralı

İç içe fonksiyonların türevini almak için kullanılır.

Örneğin:

$$
f(x)=(3x^2+1)^5
$$

Burada dış fonksiyon:

$$
u^5
$$

iç fonksiyon:

$$
u=3x^2+1
$$

Zincir kuralı:

$$
\boxed{
\frac{d}{dx}f(g(x))
=
f'(g(x))g'(x)
}
$$

Pratik olarak:

> **Dışın türevi × için türevi**

Örneğimiz:

$$
f'(x)
=
5(3x^2+1)^4\cdot6x
$$

$$
\boxed{
f'(x)=30x(3x^2+1)^4
}
$$

### Çok önemli

Zincir kuralı özellikle:

$$
(\text{bir şey})^n
$$

şeklindeki ifadelerde çok sık kullanılır.

Örneğin:

$$
(2x+5)^7
$$

$$
=7(2x+5)^6\cdot2
$$

$$
=14(2x+5)^6
$$

---

# 13. Üstel Fonksiyonların Türevi

### \(e^x\)

$$
\boxed{
\frac{d}{dx}e^x=e^x
}
$$

Bu fonksiyonun özel özelliği:

> Türevi kendisine eşittir.

### Genel üstel fonksiyon

$$
a^x
$$

için:

$$
\boxed{
\frac{d}{dx}a^x=a^x\ln a
}
$$

Örneğin:

$$
f(x)=2^x
$$

$$
f'(x)=2^x\ln2
$$

---

# 14. Logaritmanın Türevi

Doğal logaritma:

$$
\boxed{
\frac{d}{dx}\ln x=\frac1x
}
$$

Genel logaritma:

$$
\boxed{
\frac{d}{dx}\log_a x
=
\frac{1}{x\ln a}
}
$$

### Zincir kuralıyla

$$
f(x)=\ln(3x^2+1)
$$

ise:

$$
f'(x)
=
\frac{1}{3x^2+1}\cdot6x
$$

$$
\boxed{
f'(x)=\frac{6x}{3x^2+1}
}
$$

---

# 15. Trigonometrik Fonksiyonların Türevleri

En temel trigonometrik türevler:

$$
\boxed{
(\sin x)'=\cos x
}
$$

$$
\boxed{
(\cos x)'=-\sin x
}
$$

$$
\boxed{
(\tan x)'=\sec^2x
}
$$

$$
\boxed{
(\cot x)'=-\csc^2x
}
$$

$$
\boxed{
(\sec x)'=\sec x\tan x
}
$$

$$
\boxed{
(\csc x)'=-\csc x\cot x
}
$$

### Zincir kuralıyla

$$
f(x)=\sin(3x)
$$

$$
f'(x)=3\cos(3x)
$$

Çünkü:

$$
\text{dışın türevi}\times\text{için türevi
$$

---

# 16. Temel Türev Tablosu

| Fonksiyon  | Türevi            |
| ---------- | ----------------- |
| \(c\)      | \(0\)             |
| \(x^n\)    | \(nx^{n-1}\)      |
| \(e^x\)    | \(e^x\)           |
| \(a^x\)    | \(a^x\ln a\)      |
| \(\ln x\)  | \(\frac1x\)       |
| \(\sin x\) | \(\cos x\)        |
| \(\cos x\) | \(-\sin x\)       |
| \(\tan x\) | \(\sec^2x\)       |
| \(\cot x\) | \(-\csc^2x\)      |
| \(\sec x\) | \(\sec x\tan x\)  |
| \(\csc x\) | \(-\csc x\cot x\) |

---

# 17. Türev Alırken Genel Strateji

Bir fonksiyon gördüğünde önce **hangi yapıda olduğunu belirle.**

### 1. Toplama / çıkarma

$$
x^3+2x^2-5x
$$

→ Terim terim türev al.

### 2. Sabit katsayı

$$
5x^4
$$

→ Katsayıyı dışarıda tut.

### 3. Çarpım

$$
x^2\sin x
$$

→ Çarpım kuralı.

### 4. Bölüm

$$
\frac{x^2+1}{x-3}
$$

→ Bölüm kuralı.

### 5. İç içe fonksiyon

$$
(2x+1)^5
$$

→ Zincir kuralı.

### 6. Birden fazla yapı

Örneğin:

$$
f(x)=x^2\sin(3x)
$$

Burada hem **çarpım** hem de içeride **zincir kuralı** vardır.

Önce ana yapıyı belirle:

$$
u=x^2,\quad v=\sin(3x)
$$

Sonra:

$$
f'=u'v+uv'
$$

$$
f'=2x\sin(3x)+x^2(3\cos(3x))
$$

---

# 18. Bir Noktadaki Türev

Türev fonksiyonunu bulduktan sonra belirli bir noktadaki türevi hesaplayabiliriz.

Örneğin:

$$
f(x)=x^2
$$

$$
f'(x)=2x
$$

\(x=3\) noktasındaki türev:

$$
f'(3)=2(3)=6
$$

Yani:

$$
\boxed{f'(3)=6}
$$

Bu, \(x=3\) noktasındaki grafiğin teğet eğiminin 6 olduğu anlamına gelir.

---

# 19. Teğet Doğrusu

Bir fonksiyonun:

$$
x=a
$$

noktasındaki teğet doğrusunu bulmak için:

### 1. Noktayı bul

$$
y_0=f(a)
$$

### 2. Eğimi bul

$$
m=f'(a)
$$

### 3. Nokta-eğim formülünü kullan

$$
\boxed{
y-y_0=f'(a)(x-a)
}
$$

Örneğin:

$$
f(x)=x^2
$$

\(x=2\) noktasındaki teğet:

Nokta:

$$
f(2)=4
$$

Yani:

$$
(2,4)
$$

Eğim:

$$
f'(x)=2x
$$

$$
f'(2)=4
$$

Dolayısıyla:

$$
y-4=4(x-2)
$$

$$
\boxed{y=4x-4}
$$

---

# 20. Türevin Fiziksel Anlamı

Türev yalnızca grafiklerde kullanılmaz.

## Konum → Hız

$$
\boxed{v(t)=s'(t)}
$$

## Hız → İvme

$$
\boxed{a(t)=v'(t)=s''(t)}
$$

Dolayısıyla:

$$
s(t)
\rightarrow
v(t)
\rightarrow
a(t)
$$

şeklinde ilerleriz.

Örneğin:

$$
s(t)=t^3
$$

ise:

$$
v(t)=3t^2
$$

ve:

$$
a(t)=6t
$$

---

# 21. Birinci ve İkinci Türev

### Birinci türev

$$
f'(x)
$$

fonksiyonun değişim hızını gösterir.

### İkinci türev

$$
f''(x)
$$

birinci türevin türevidir:

$$
\boxed{
f''(x)=\frac{d}{dx}f'(x)
}
$$

Genel olarak:

$$
f^{(n)}(x)
$$

\(n\)'inci türevi ifade eder.

Örneğin:

$$
f(x)=x^4
$$

$$
f'(x)=4x^3
$$

$$
f''(x)=12x^2
$$

$$
f'''(x)=24x
$$

$$
f^{(4)}(x)=24
$$

$$
f^{(5)}(x)=0
$$

---

# 22. Artan ve Azalan Fonksiyonlar

Türev, fonksiyonun hangi bölgelerde arttığını veya azaldığını belirlememizi sağlar.

Genel olarak:

$$
\boxed{f'(x)>0\Rightarrow f \text{ artan}}
$$

$$
\boxed{f'(x)<0\Rightarrow f \text{ azalan}}
$$

Örneğin:

$$
f(x)=x^2
$$

$$
f'(x)=2x
$$

### \(x<0\)

$$
2x<0
$$

Fonksiyon azalır.

### \(x>0\)

$$
2x>0
$$

Fonksiyon artar.

Bu nedenle \(x=0\) civarında fonksiyonun davranışı değişir.

---

# 23. Kritik Noktalar

Bir fonksiyonda:

$$
f'(x)=0
$$

olan noktalar veya türevin tanımsız olduğu noktalar **kritik noktalar** olarak incelenir.

Örneğin:

$$
f(x)=x^2
$$

$$
f'(x)=2x
$$

$$
2x=0
$$

$$
x=0
$$

kritik noktadır.

Kritik noktalar özellikle:

* maksimum
* minimum
* artma-azalma
* optimizasyon

problemlerinde önemlidir.

> Her \(f'(x)=0\) noktası otomatik olarak maksimum veya minimum değildir.

---

# 24. Yerel Maksimum ve Minimum

Bir fonksiyon önce artıp sonra azalıyorsa:

$$
+\rightarrow-
$$

o noktada **yerel maksimum** olabilir.

Bir fonksiyon önce azalıp sonra artıyorsa:

$$
-\rightarrow+
$$

o noktada **yerel minimum** olabilir.

Türev işaret tablosu bu nedenle önemlidir.

### Birinci türev testi

$$
f'(x):
$$

$$
+\rightarrow-
$$

→ yerel maksimum

$$
-\rightarrow+
$$

→ yerel minimum

Ancak:

$$
+\rightarrow+
$$

veya

$$
-\rightarrow-
$$

gibi durumlarda \(f'(x)=0\) olmasına rağmen ekstremum olmayabilir.

---

# 25. İkinci Türev ve Konkavlık

İkinci türev, grafiğin **konkavlığını** incelememizi sağlar.

Genel olarak:

$$
f''(x)>0
$$

ise grafik **yukarı doğru konkav**.

$$
f''(x)<0
$$

ise grafik **aşağı doğru konkav**.

Bu kavram özellikle grafik analizinde ve ikinci türev testinde kullanılır.

---

# 26. İkinci Türev Testi

Bir noktada:

$$
f'(a)=0
$$

olsun.

Eğer:

$$
f''(a)>0
$$

ise:

$$
\boxed{\text{yerel minimum}}
$$

olabilir.

Eğer:

$$
f''(a)<0
$$

ise:

$$
\boxed{\text{yerel maksimum}}
$$

olabilir.

Eğer:

$$
f''(a)=0
$$

ise bu test **sonuç vermez**.

---

# 27. Türevin Tanımlı Olması

Bir fonksiyonun bir noktada türevlenebilir olması için o noktada belirli koşulların sağlanması gerekir.

Özellikle:

$$
\boxed{\text{Türevlenebilirlik}\Rightarrow\text{Süreklilik}}
$$

Yani bir fonksiyon bir noktada türevlenebilirse o noktada süreklidir.

Fakat tersi her zaman doğru değildir:

$$
\boxed{\text{Süreklilik}\not\Rightarrow\text{Türevlenebilirlik}}
$$

Örneğin:

$$
f(x)=|x|
$$

fonksiyonu \(x=0\)'da süreklidir fakat burada keskin bir köşe bulunduğu için türevlenemez.

---

# 28. Sol ve Sağ Türev

Bir noktadaki türevi incelerken sol ve sağ taraftan yaklaşabiliriz.

Sol türev:

$$
f'_-(a)
$$

Sağ türev:

$$
f'_+(a)
$$

Türevli olabilmesi için:

$$
\boxed{
f'_-(a)=f'_+(a)
}
$$

olmalıdır.

$$
|x|
$$

için \(x=0\)'da:

$$
f'_-(0)=-1
$$

$$
f'_+(0)=1
$$

olduğu için:

$$
f'_-(0)\neq f'_+(0)
$$

ve dolayısıyla:

$$
\boxed{|x|\text{, }x=0\text{'da türevlenemez.}}
$$

---

# 29. Türev ile Limit Arasındaki İlişki

Türev doğrudan limit kavramından ortaya çıkar:

$$
\boxed{
f'(x)=
\lim_{h\to0}
\frac{f(x+h)-f(x)}{h}
}
$$

Bu nedenle türev öğrenirken limitin mantığını anlamak önemlidir.

Temel bağlantı:

$$
\boxed{
\text{Limit}
\rightarrow
\text{Türev}
\rightarrow
\text{Değişim / Teğet / Optimizasyon}
}
$$

---

# 30. En Önemli Formüller

### Türev tanımı

$$
\boxed{
f'(x)=
\lim_{h\to0}
\frac{f(x+h)-f(x)}{h}
}
$$

### Kuvvet

$$
\boxed{
(x^n)'=nx^{n-1}
}
$$

### Toplam

$$
\boxed{
(f+g)'=f'+g'
}
$$

### Sabit katsayı

$$
\boxed{
(cf)'=cf'
}
$$

### Çarpım

$$
\boxed{
(fg)'=f'g+fg'
}
$$

### Bölüm

$$
\boxed{
\left(\frac fg\right)'
=
\frac{f'g-fg'}{g^2}
}
$$

### Zincir

$$
\boxed{
(f(g(x)))'=f'(g(x))g'(x)
}
$$

### Üstel

$$
\boxed{
(e^x)'=e^x
}
$$

$$
\boxed{
(a^x)'=a^x\ln a
}
$$

### Logaritma

$$
\boxed{
(\ln x)'=\frac1x
}
$$

### Trigonometri

$$
\boxed{
(\sin x)'=\cos x
}
$$

$$
\boxed{
(\cos x)'=-\sin x
}
$$

$$
\boxed{
(\tan x)'=\sec^2x
}
$$

---

# 31. Türev Problemlerinde Düşünme Sırası

Bir türev sorusu gördüğümde:

1. **Fonksiyonun yapısını belirle.**
2. Basit polinomsa → **kuvvet kuralı**
3. Toplama/çıkarma varsa → **terim terim türev**
4. Çarpım varsa → **çarpım kuralı**
5. Bölüm varsa → **bölüm kuralı**
6. İç içe fonksiyon varsa → **zincir kuralı**
7. Trigonometrik, logaritmik veya üstel fonksiyon varsa → **temel türev tablosu**
8. Bir noktadaki değer isteniyorsa → önce türevi bul, sonra \(x\)'i yerine koy.
9. Teğet isteniyorsa → **nokta + türevden gelen eğim**
10. Artma/azalma isteniyorsa → **\(f'(x)\)'in işaretini incele**
11. Maksimum/minimum isteniyorsa → **kritik noktaları bul ve işaret değişimini incele**
12. Konkavlık isteniyorsa → **\(f''(x)\)'e bak**

---

# 32. Türevi Tek Cümlede Özetlersek

> **Türev, bir fonksiyonun bir noktadaki anlık değişim hızıdır ve geometrik olarak o noktadaki teğet doğrusunun eğimini verir.**

Bütün konu aslında şu fikirden büyür:

$$
\boxed{
\text{Ortalama değişim}
\overset{h\to0}{\longrightarrow}
\text{Anlık değişim}
}
$$

ve:

$$
\boxed{
\text{Sekant eğimi}
\overset{h\to0}{\longrightarrow}
\text{Teğet eğimi}
}
$$

---

# Hızlı Tekrar

**Türev = değişim hızı = teğet eğimi**

$$
f'(x)=
\lim_{h\to0}
\frac{f(x+h)-f(x)}{h}
$$

En önemli kurallar:

$$
(x^n)'=nx^{n-1}
$$

$$
(fg)'=f'g+fg'
$$

$$
\left(\frac fg\right)'
=
\frac{f'g-fg'}{g^2}
$$

$$
(f(g(x)))'=f'(g(x))g'(x)
$$

Ve temel yorum:

$$
f'>0 \Rightarrow \text{artan}
$$

$$
f'<0 \Rightarrow \text{azalan}
$$

$$
f'=0 \Rightarrow \text{kritik nokta adayı}
$$

$$
f''>0 \Rightarrow \text{yukarı konkav}
$$

$$
f''<0 \Rightarrow \text{aşağı konkav}
$$

> [!important]
> Türevde asıl amaç formülleri ezberlemekten önce **fonksiyonun nasıl değiştiğini okuyabilmek**. Formüller bu fikri hızlı hesaplamaya dönüştüren araçlardır.

