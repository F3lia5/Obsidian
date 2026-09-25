# Fizik ve Ölçme

> [!abstract] Konu
> Fizikte kullanılan temel büyüklükler, SI birim sistemi, ölçme, boyut analizi, birim dönüşümleri, bilimsel gösterim, vektörlerin bileşenleri, yoğunluk, hacim ve mol kavramı.

---

## 1. Fizik Nedir?

**Fizik**, doğadaki madde, enerji, hareket, kuvvet, elektrik, manyetizma, dalgalar vb. olayları matematiksel modeller kullanarak inceleyen bilim dalıdır.

Fizikte bir fiziksel büyüklüğü ifade etmek için genellikle iki şey gerekir:

$$
\boxed{\text{Fiziksel büyüklük} = \text{sayısal değer} \times \text{birim}}
$$

Örneğin:

$$
5\,m
$$

Burada:

* `5` → sayısal değer
* `m` → metre, yani birim

**Birim olmadan fiziksel ölçüm eksik kalır.**

---

# 2. SI Birim Sistemi

Fizikte dünyada ortak bir ölçüm dili kullanmak için **SI (Système International d'Unités)** birim sistemi kullanılır.

SI'da **7 temel birim** vardır:

| Fiziksel büyüklük     | SI birimi | Sembol |
| --------------------- | --------- | ------ |
| Uzunluk               | metre     | `m`    |
| Kütle                 | kilogram  | `kg`   |
| Zaman                 | saniye    | `s`    |
| Elektrik akımı        | amper     | `A`    |
| Termodinamik sıcaklık | kelvin    | `K`    |
| Madde miktarı         | mol       | `mol`  |
| Işık şiddeti          | candela   | `cd`   |

Bunlardan türetilen büyüklüklere **türetilmiş büyüklükler** denir.

Örneğin hız:

$$
v=\frac{x}{t}
$$

Birim olarak:

$$
[v]=\frac{m}{s}
$$

Kuvvet:

$$
F=ma
$$

olduğundan:

$$
[F]=kg\cdot\frac{m}{s^2}
$$

Bu birime özel olarak **Newton (N)** denir:

$$
1N=1\,kg\cdot m/s^2
$$

> [!important]
> Fizikte formülleri öğrenirken yalnızca sayıları değil, **birimleri de takip etmek** çok önemlidir.

---

# 3. SI Birimlerinin Güncel Tanımları

SI'ın modern sisteminde birimler belirli fiziksel sabitlerin **tam olarak belirlenmiş değerleri** üzerinden tanımlanır. Bu sistem 20 Mayıs 2019'da yürürlüğe giren SI revizyonuyla kullanılmaktadır.

## 3.1 Metre — `m`

Metre, boşlukta ışığın aldığı yol üzerinden tanımlanır.

Işığın boşluktaki hızı:

$$
\boxed{c=299\,792\,458\ m/s}
$$

Bu nedenle:

$$
\boxed{1\,m=\text{ışığın boşlukta } \frac{1}{299\,792\,458}\text{ saniyede aldığı yol}}
$$

> [!note]
> Dersteki "`1/300 saniyede ışığın aldığı yol`" ifadesi yaklaşık bir anlatımdır.
>
> **Tam tanım:**
>
> $$
> \frac{1}{299\,792\,458}\ s
> $$

Bu tanımın önemli özelliği, ışık hızının değerinin **tam olarak** belirlenmiş olmasıdır.

---

## 3.2 Saniye — `s`

Saniyenin tanımında **Sezyum-133 (`^{133}Cs`) atomu** kullanılır.

Sezyum-133 atomunun belirli bir enerji geçişine karşılık gelen frekans:

$$
\boxed{\Delta\nu_{Cs}=9\,192\,631\,770\ Hz}
$$

Dolayısıyla:

$$
\boxed{1s=9\,192\,631\,770\text{ periyot}}
$$

Buradaki geçiş, Sezyum-133 atomunun temel hâlinin iki hiperince enerji seviyesi arasındaki geçiştir.

> [!warning]
> "Sezyum atomu 9 milyar kez titreşiyor" demek günlük anlatım açısından kullanılabilir ama teknik olarak daha doğru ifade **belirli bir atomik geçişin 9 192 631 770 periyodu** şeklindedir.

---

## 3.3 Kilogram — `kg`

Burada önemli bir güncelleme var.

### Eski tanım

Eskiden kilogram, **platin-iridyum alaşımından yapılmış uluslararası prototip kilogramın kütlesi** üzerinden tanımlanıyordu.

Yani derste duyduğun:

> "Platin-iridyum silindirinin kütlesi 1 kg'dır."

ifadesi **eski tanımdır**.

### Güncel tanım

2019'dan beri kilogram, **Planck sabiti `h`** üzerinden tanımlanmaktadır:

$$
\boxed{h=6.626\,070\,15\times10^{-34}\ J\,s}
$$

Bu değer tam olarak sabitlenmiştir. Kilogram da bu sabit üzerinden türetilir.

> [!important]
> **Sınav açısından:**
>
> * Eski sistem → platin-iridyum prototipi
> * Güncel SI → Planck sabiti
>
> Hocanız eski tanımı özellikle anlattıysa, tarihsel bilgi olarak bilmek faydalıdır.

---

# 4. Boyut (Dimension) Kavramı

Fiziksel büyüklüklerin hangi temel büyüklüklere bağlı olduğunu göstermek için **boyut analizi** kullanılır.

Temel boyutlar:

* Uzunluk → `[L]`
* Kütle → `[M]`
* Zaman → `[T]`

Diğer fiziksel büyüklüklerin boyutları bunlardan türetilebilir.

---

## 4.1 Hızın Boyutu

Hız:

$$
v=\frac{x}{t}
$$

Uzunluğun boyutu:

$$
[x]=[L]
$$

Zamanın boyutu:

$$
[t]=[T]
$$

Dolayısıyla:

$$
\boxed{[v]=\frac{[L]}{[T]}=[L][T]^{-1}}
$$

---

## 4.2 Boyut Analizi ile Formül Kontrolü

Örneğin:

$$
x=v\cdot t
$$

Boyutlarına bakalım:

$$
[x]=[v][t]
$$

$$
[x]=\frac{[L]}{[T]}\cdot[T]
$$

$$
\boxed{[x]=[L]}
$$

Sol taraf ve sağ taraf aynı boyuta sahip.

Bu nedenle denklem **boyutsal olarak tutarlıdır**.

> [!important]
>
> ### SINAVLIK
>
> Bir fizik denkleminin doğru olup olmadığını kontrol etmek için **boyut analizi** kullanılabilir.
>
> Örneğin:
>
> $$
> x=v t
> $$
>
> için:
>
> $$
> [L]=[L/T][T]=[L]
> $$
>
> olduğundan denklem boyutsal olarak doğrudur.

---

# 5. Boyut Analizi ile Formül Bulma

Boyut analizi yalnızca formül kontrol etmek için değil, bazı durumlarda formülün nasıl olması gerektiğini tahmin etmek için de kullanılabilir.

Örneğin basit sarkaç periyodunun:

$$
T\propto \sqrt{\frac{L}{g}}
$$

şeklinde olması boyutlardan anlaşılabilir.

Çünkü:

$$
[g]=\frac{L}{T^2}
$$

olduğundan:

$$
\frac{L}{g}
=
\frac{L}{L/T^2}
=T^2
$$

ve:

$$
\sqrt{T^2}=T
$$

çıkar.

> [!note]
> Boyut analizi **sayısal katsayıları** (`2`, `π`, `1/2` gibi) belirleyemez. Yalnızca birim/boyut açısından hangi yapıların mümkün olduğunu gösterir.

---

# 6. Skaler ve Vektörel Büyüklükler

Fiziksel büyüklükler genel olarak ikiye ayrılır.

## Skaler

Yalnızca **büyüklüğü** vardır.

Örnekler:

* Kütle
* Zaman
* Sıcaklık
* Enerji
* Sürat
* Yoğunluk
* Hacim

Örneğin:

$$
5\,kg
$$

---

## Vektörel

Hem **büyüklüğü hem yönü** vardır.

Örnekler:

* Konum
* Hız
* İvme
* Kuvvet
* Momentum

Örneğin:

$$
\vec{v}=20\,m/s\text{ doğuya}
$$

Burada `20 m/s` büyüklük, **doğu** ise yöndür.

> [!warning]
> Fizikte **sürat** ve **hız** aynı şey değildir.
>
> * Sürat → skaler
> * Hız → vektörel

---

# 7. Vektörlerin Bileşenlerine Ayrılması

Bir vektör, birbirine dik iki bileşene ayrılabilir.

Bir vektörün büyüklüğü:

$$
r
$$

ve x ekseniyle yaptığı açı:

$$
\theta
$$

ise:

$$
\boxed{x=r\cos\theta}
$$

$$
\boxed{y=r\sin\theta}
$$

Burada:

* `r` → vektörün büyüklüğü
* `x` → x bileşeni
* `y` → y bileşeni
* `θ` → vektörün x ekseniyle yaptığı açı

## Neden cos ve sin?

Dik üçgende:

$$
\cos\theta=\frac{\text{komşu kenar}}{\text{hipotenüs}}
$$

Dolayısıyla:

$$
\cos\theta=\frac{x}{r}
$$

Buradan:

$$
\boxed{x=r\cos\theta}
$$

Benzer şekilde:

$$
\sin\theta=\frac{\text{karşı kenar}}{\text{hipotenüs}}
$$

$$
\sin\theta=\frac{y}{r}
$$

Buradan:

$$
\boxed{y=r\sin\theta}
$$

---

## Vektörün Büyüklüğünü Bileşenlerden Bulma

Elimizde `x` ve `y` bileşenleri varsa Pisagor teoremi:

$$
\boxed{r=\sqrt{x^2+y^2}}
$$

kullanılır.

Açı:

$$
\boxed{\theta=\tan^{-1}\left(\frac{y}{x}\right)}
$$

ile bulunabilir.

> [!important]
> Vektör bileşenlerinde en önemli üçlü:
>
> $$
> \boxed{x=r\cos\theta}
> $$
>
> $$
> \boxed{y=r\sin\theta}
> $$
>
> $$
> \boxed{r=\sqrt{x^2+y^2}}
> $$

---

# 8. Ölçme

**Ölçme**, bir fiziksel büyüklüğün belirli bir standartla karşılaştırılmasıdır.

Örneğin bir masanın uzunluğunu ölçerken:

$$
L=1.20\,m
$$

diyorsak masanın uzunluğunu metre standardıyla karşılaştırmış oluruz.

Her ölçümde şu kavramlar önemlidir:

* Ölçülen büyüklük
* Ölçü aleti
* Birim
* Ölçüm sonucu
* Belirsizlik

---

# 9. Ölçüm Belirsizliği

Gerçek hayatta hiçbir ölçüm sonsuz hassasiyetle yapılamaz.

Örneğin bir cetvelin en küçük bölmesi `1 mm` ise, ölçümümüz bu hassasiyetle sınırlıdır.

Bu nedenle:

$$
L=10.2\,cm
$$

ile

$$
L=10.200000\,cm
$$

aynı anlamı taşımaz.

İkinci ifade çok daha yüksek hassasiyet iddiasında bulunur.

> [!important]
> Ölçüm sonucunda yazılan basamaklar, ölçümün **hassasiyeti hakkında bilgi taşır.**

---

# 10. Anlamlı Rakamlar

Bir ölçümdeki anlamlı rakamlar, ölçümün içerdiği güvenilir bilgi miktarını ifade eder.

Örneğin:

$$
2.35\,m
$$

3 anlamlı rakama sahiptir.

### Temel kurallar

* Sıfır olmayan rakamlar anlamlıdır.
* İki anlamlı rakam arasındaki sıfırlar anlamlıdır.
* Ondalık sayının başındaki sıfırlar genellikle anlamlı değildir.

Örneğin:

$$
0.0045
$$

→ 2 anlamlı rakam.

Ama:

$$
4.050
$$

→ 4 anlamlı rakam.

> [!note]
> Anlamlı rakam konusu ileride ölçüm, deney ve hata hesaplarında sık sık karşımıza çıkacaktır.

---

# 11. Bilimsel Gösterim

Çok büyük veya çok küçük sayıları yazmak için bilimsel gösterim kullanılır.

Genel biçim:

$$
\boxed{a\times10^n}
$$

Burada:

$$
1\leq |a|<10
$$

Örnek:

$$
300\,000\,000
=
3\times10^8
$$

$$
0.0000045
=
4.5\times10^{-6}
$$

Fizikte bu gösterim özellikle çok büyük ve çok küçük ölçeklerde kullanılır.

Örneğin:

$$
c=2.99792458\times10^8\,m/s
$$

---

# 12. SI Ön Ekleri

Birimleri büyük veya küçük miktarlarda ifade etmek için ön ekler kullanılır.

| Ön ek | Sembol |     Çarpan |
| ----- | -----: | ---------: |
| kilo  |      k |     $10^3$ |
| mega  |      M |     $10^6$ |
| giga  |      G |     $10^9$ |
| tera  |      T |  $10^{12}$ |
| mili  |      m |  $10^{-3}$ |
| mikro |  $\mu$ |  $10^{-6}$ |
| nano  |      n |  $10^{-9}$ |
| piko  |      p | $10^{-12}$ |

Örnek:

$$
1\,km=10^3\,m
$$

$$
1\,mm=10^{-3}\,m
$$

$$
1\,\mu m=10^{-6}\,m
$$

---

# 13. Birim Dönüşümü

Birim dönüşümlerinde temel amaç fiziksel büyüklüğü değiştirmeden yalnızca kullandığımız birimi değiştirmektir.

Örneğin:

$$
1\,km=1000\,m
$$

Dolayısıyla:

$$
3.5\,km
=
3.5\times1000
=
3500\,m
$$

### Alan ve hacimde dikkat

Uzunluk dönüşümünde:

$$
1\,cm=10^{-2}\,m
$$

Ancak alan:

$$
1\,cm^2=(10^{-2}m)^2
$$

$$
\boxed{1\,cm^2=10^{-4}\,m^2}
$$

Hacim:

$$
1\,cm^3=(10^{-2}m)^3
$$

$$
\boxed{1\,cm^3=10^{-6}\,m^3}
$$

> [!warning]
> `cm → m` dönüşümünde $10^{-2}$ kullanılırken:
>
> `cm² → m²` için $10^{-4}$,
>
> `cm³ → m³` için $10^{-6}$ kullanılır.
>
> Çünkü üs de dönüşüme uygulanır.

---

# 14. Yoğunluk

Yoğunluk, bir maddenin birim hacmindeki kütlesidir.

$$
\boxed{\rho=\frac{m}{V}}
$$

Burada:

* `ρ` → yoğunluk
* `m` → kütle
* `V` → hacim

Buradan diğer iki büyüklük:

$$
\boxed{m=\rho V}
$$

$$
\boxed{V=\frac{m}{\rho}}
$$

### Yoğunluk birimleri

SI birimi:

$$
\boxed{kg/m^3}
$$

Sık kullanılan başka bir birim:

$$
g/cm^3
$$

Aralarındaki dönüşüm:

$$
\boxed{1\,g/cm^3=1000\,kg/m^3}
$$

---

# 15. Kütle - Hacim - Yoğunluk Problemleri

Bir cismin kütlesi ve hacmi verilirse yoğunluğu:

$$
\rho=\frac{m}{V}
$$

ile bulunur.

Örneğin:

Bir alüminyum küpün:

$$
m=270\,g
$$

ve bir kenar uzunluğu:

$$
a=5\,cm
$$

olsun.

Küpün hacmi:

$$
V=a^3
$$

$$
V=5^3=125\,cm^3
$$

Yoğunluk:

$$
\rho=\frac{270}{125}
$$

$$
\boxed{\rho=2.16\,g/cm^3}
$$

> [!note]
> Gerçek alüminyumun yoğunluğu yaklaşık `2.70 g/cm³` olduğundan, bu örnekteki değer **gerçekçi bir ölçüm örneği değildir**; yöntem göstermek için kullanılmıştır.

### Gerçekçi örnek

Alüminyumun yoğunluğunu:

$$
\rho\approx2.70\,g/cm^3
$$

kabul edersek, kenarı `5 cm` olan bir küpün:

$$
V=125\,cm^3
$$

olur.

Dolayısıyla:

$$
m=\rho V
$$

$$
m=(2.70)(125)
$$

$$
\boxed{m=337.5\,g}
$$

Bu tarz sorularda temel sıra:

$$
\boxed{\text{Geometrik hacmi bul}\rightarrow\text{Yoğunluk formülünü kullan}}
$$

---

# 16. Geometrik Hacim Formülleri

Yoğunluk problemlerinde cismin hacmini bulabilmek çok önemlidir.

## Küp

Kenar uzunluğu `a`:

$$
\boxed{V=a^3}
$$

---

## Dikdörtgenler Prizması

Kenarlar `a`, `b`, `c`:

$$
\boxed{V=abc}
$$

---

## Silindir

Yarıçap `r`, yükseklik `h`:

$$
\boxed{V=\pi r^2h}
$$

---

## Koni

Yarıçap `r`, yükseklik `h`:

$$
\boxed{V=\frac13\pi r^2h}
$$

---

## Küre

Yarıçap `r`:

$$
\boxed{V=\frac43\pi r^3}
$$

---

# 17. Hacim Formüllerini Hatırlama

Temel fikir:

### Silindir

Daire alanı × yükseklik:

$$
V=\pi r^2h
$$

### Koni

Aynı taban ve yüksekliğe sahip silindirin üçte biri:

$$
V=\frac13\pi r^2h
$$

### Küre

$$
V=\frac43\pi r^3
$$

> [!important]
> Özellikle yoğunluk sorularında önce **hacim**, sonra **yoğunluk/kütle** hesabı yapılır.

---

# 18. Mol ve Avogadro Sayısı

**Mol**, maddenin miktarını ifade eden SI temel birimidir.

Bir mol herhangi bir türden tam olarak:

$$
\boxed{6.022\,140\,76\times10^{23}}
$$

tane temel parçacık içerir.

Bu sayı **Avogadro sabiti** olarak adlandırılır:

$$
\boxed{N_A=6.022\,140\,76\times10^{23}\ mol^{-1}}
$$

Parçacık:

* atom
* molekül
* iyon
* elektron
* vb.

olabilir.

Örneğin:

$$
1\,mol\ H_2O
$$

tam olarak:

$$
6.022\,140\,76\times10^{23}
$$

adet su molekülü içerir.

---

## Mol - Parçacık Sayısı İlişkisi

Parçacık sayısı `N`, mol sayısı `n` ise:

$$
\boxed{N=nN_A}
$$

Buradan:

$$
\boxed{n=\frac{N}{N_A}}
$$

elde edilir.

---

# 19. Mol ve Kütle İlişkisi

Mol sayısı ile kütle arasındaki ilişki:

$$
\boxed{n=\frac{m}{M}}
$$

Burada:

* `n` → mol sayısı
* `m` → kütle
* `M` → molar kütle

Buradan:

$$
\boxed{m=nM}
$$

---

# 20. Fizikte Birimlerin Takibi

Bir problem çözerken yalnızca sayıları değil, **birimleri de işlem içine dahil etmek** gerekir.

Örneğin:

$$
v=\frac{x}{t}
$$

$$
x=20\,m
$$

$$
t=4\,s
$$

ise:

$$
v=\frac{20\,m}{4\,s}
$$

$$
\boxed{v=5\,m/s}
$$

Birimler işlemin sonunda fiziksel büyüklüğün ne olduğunu gösterir.

---

# 21. Boyutlar ile SI Birimleri Arasındaki Fark

Bu ikisi birbirine karıştırılmamalıdır.

### Birim

Örneğin hızın SI birimi:

$$
m/s
$$

### Boyut

Hızın boyutu:

$$
[L][T]^{-1}
$$

Yani:

$$
\boxed{\text{Birim}\neq\text{Boyut}}
$$

Örneğin hız:

$$
km/h
$$

ile de ifade edilebilir.

Ama boyutu her zaman:

$$
[L][T]^{-1}
$$

olarak kalır.

---

# 22. Temel Boyutlardan Bazı Türetilmiş Boyutlar

## Alan

$$
A=L^2
$$

$$
\boxed{[A]=[L]^2}
$$

## Hacim

$$
V=L^3
$$

$$
\boxed{[V]=[L]^3}
$$

## Hız

$$
v=\frac{x}{t}
$$

$$
\boxed{[v]=[L][T]^{-1}}
$$

## İvme

$$
a=\frac{\Delta v}{\Delta t}
$$

$$
\boxed{[a]=[L][T]^{-2}}
$$

## Kuvvet

$$
F=ma
$$

$$
[F]=[M][L][T]^{-2}
$$

## Yoğunluk

$$
\rho=\frac{m}{V}
$$

$$
[\rho]=\frac{[M]}{[L]^3}
$$

$$
\boxed{[\rho]=[M][L]^{-3}}
$$

---

# 23. Sınav İçin Bilinmesi Gereken Temel Formüller

## Kinematik / temel ilişkiler

$$
\boxed{v=\frac{x}{t}}
$$

$$
\boxed{x=vt}
$$

## Vektör bileşenleri

$$
\boxed{x=r\cos\theta}
$$

$$
\boxed{y=r\sin\theta}
$$

$$
\boxed{r=\sqrt{x^2+y^2}}
$$

$$
\boxed{\theta=\tan^{-1}\left(\frac{y}{x}\right)}
$$

## Yoğunluk

$$
\boxed{\rho=\frac{m}{V}}
$$

$$
\boxed{m=\rho V}
$$

$$
\boxed{V=\frac{m}{\rho}}
$$

## Hacim

$$
\boxed{V_{\text{küp}}=a^3}
$$

$$
\boxed{V_{\text{prizma}}=abc}
$$

$$
\boxed{V_{\text{silindir}}=\pi r^2h}
$$

$$
\boxed{V_{\text{koni}}=\frac13\pi r^2h}
$$

$$
\boxed{V_{\text{küre}}=\frac43\pi r^3}
$$

## Mol

$$
\boxed{N=nN_A}
$$

$$
\boxed{n=\frac{N}{N_A}}
$$

$$
\boxed{n=\frac{m}{M}}
$$

---

# 24. En Önemli Kavramlar — Hızlı Tekrar

> [!important] EZBERLENMESİ GEREKENLER

### SI temel birimleri

$$
\boxed{m,\ kg,\ s,\ A,\ K,\ mol,\ cd}
$$

### Metre

$$
\boxed{1m=\text{ışığın boşlukta }1/299\,792\,458\,s\text{ içinde aldığı yol}}
$$

### Saniye

$$
\boxed{9\,192\,631\,770\text{ Sezyum-133 geçiş periyodu}}
$$

### Kilogram

Güncel tanım:

$$
\boxed{\text{Planck sabiti }h}
$$

Eski tanım:

$$
\boxed{\text{platin-iridyum prototip}}
$$

### Mol

$$
\boxed{1mol=6.022\,140\,76\times10^{23}\text{ varlık}}
$$

### Boyutlar

$$
\boxed{[L], [M], [T]}
$$

### Hız

$$
\boxed{[v]=[L][T]^{-1}}
$$

### Yoğunluk

$$
\boxed{\rho=\frac{m}{V}}
$$

### Vektör bileşenleri

$$
\boxed{x=r\cos\theta}
$$

$$
\boxed{y=r\sin\theta}
$$

### Küp

$$
\boxed{V=a^3}
$$

### Silindir

$$
\boxed{V=\pi r^2h}
$$

### Koni

$$
\boxed{V=\frac13\pi r^2h}
$$

### Küre

$$
\boxed{V=\frac43\pi r^3}
$$

---

# 25. Konunun Genel Mantığı

Bu konunun tamamını aslında şu zincir üzerinden düşünebiliriz:

$$
\boxed{
\text{Fiziksel büyüklük}
\rightarrow
\text{ölçüm}
\rightarrow
\text{birim}
\rightarrow
\text{boyut}
\rightarrow
\text{matematiksel ilişki}
}
$$

Örneğin bir alüminyum cismin kütlesini bulmak istersek:

$$
\text{Geometri}
\rightarrow
V
$$

sonra:

$$
\text{Yoğunluk}
\rightarrow
\rho
$$

sonra:

$$
\boxed{m=\rho V}
$$

kullanılır.

Bir vektörü incelemek istersek:

$$
\text{Vektör}
\rightarrow
\text{dik üçgen}
\rightarrow
\sin/\cos
\rightarrow
\text{x-y bileşenleri}
$$

şeklinde ilerleriz.

Bir fizik denklemini kontrol etmek istersek:

$$
\text{Formül}
\rightarrow
\text{birimleri/boyutları yaz}
\rightarrow
\text{iki tarafı karşılaştır}
$$

yaparız.

> [!tip]
> Bu konunun asıl amacı formülleri ezberlemekten çok **fiziksel büyüklükleri doğru tanımlamak, doğru birimleri kullanmak ve denklemlerin fiziksel olarak tutarlı olup olmadığını kontrol edebilmek**.

---

## Kaynak

Güncel SI tanımları için **Bureau International des Poids et Mesures (BIPM)** kaynak alınmıştır. SI'ın güncel tanımları ve 2019 revizyonu özellikle metre, saniye, kilogram ve mol bölümlerinde esas alınmıştır.

