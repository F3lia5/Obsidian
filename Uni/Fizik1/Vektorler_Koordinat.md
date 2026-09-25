# Fizik 2 — Vektörler ve Koordinat Sistemleri

> [!abstract] Konu
> Kartezyen koordinat sistemi, noktaların gösterimi, orta nokta, kutupsal koordinat sistemi, Kartezyen ↔ kutupsal dönüşümler, vektörlerin gösterimi, bileşenleri, büyüklüğü, yönü, birim vektörler ve temel vektör işlemleri.

---

# 1. Koordinat Sistemi Nedir?

Bir cismin veya noktanın uzaydaki konumunu tanımlayabilmek için bir **koordinat sistemi** seçeriz.

İki boyutlu düzlemde en sık kullanılan sistem:

$$
\boxed{\text{Kartezyen (Cartesian) koordinat sistemi}}
$$

Bu sistemde iki eksen vardır:

* `x` ekseni → yatay
* `y` ekseni → dikey

Eksenlerin kesiştiği nokta:

$$
\boxed{(0,0)}
$$

ve buna **orijin (origin)** denir.

---

# 2. Kartezyen Koordinat Sistemi

Bir noktanın koordinatı:

$$
\boxed{P=(x,y)}
$$

şeklinde gösterilir.

Örneğin:

$$
P=(3,2)
$$

demek:

* x yönünde `3`
* y yönünde `2`

birim ileride bulunan nokta demektir.

## İşaretler

| Bölge      |  x |  y |
| ---------- | -: | -: |
| I. bölge   |  + |  + |
| II. bölge  |  - |  + |
| III. bölge |  - |  - |
| IV. bölge  |  + |  - |

Basitçe:

```text
              +y
               ↑
        II     |     I
               |
  -x ←---------+---------→ +x
               |
        III    |     IV
               ↓
              -y
```

> [!important]
> Bir noktanın koordinatında **önce x, sonra y** yazılır:
>
> $$
> (x,y)
> $$
>
> `(y,x)` yazmak farklı bir noktayı ifade eder.

---

# 3. İki Nokta Arasındaki Uzaklık

İki nokta:

$$
P_1=(x_1,y_1)
$$

$$
P_2=(x_2,y_2)
$$

olsun.

Aralarındaki yatay fark:

$$
\Delta x=x_2-x_1
$$

Dikey fark:

$$
\Delta y=y_2-y_1
$$

Bu iki fark bir dik üçgen oluşturur.

Pisagor teoreminden:

$$
d^2=(\Delta x)^2+(\Delta y)^2
$$

dolayısıyla:

$$
\boxed{
d=\sqrt{(x_2-x_1)^2+(y_2-y_1)^2}
}
$$

Bu formül ileride **vektörün büyüklüğünü** bulurken de karşımıza çıkacak.

---

# 4. İki Noktanın Orta Noktası

İki noktanın tam ortasındaki noktayı bulmak için x koordinatlarının ortalaması ve y koordinatlarının ortalaması alınır.

Noktalar:

$$
P_1=(x_1,y_1)
$$

$$
P_2=(x_2,y_2)
$$

ise orta nokta:

$$
\boxed{
M=
\left(
\frac{x_1+x_2}{2},
\frac{y_1+y_2}{2}
\right)
}
$$

> [!warning]
> Formülü şöyle yazmak yanlış anlaşılabilir:
>
> $$
> (x_1+x_2/2)
> $$
>
> Doğrusu:
>
> $$
> \boxed{\frac{x_1+x_2}{2}}
> $$
>
> Yani **toplamın tamamı 2'ye bölünür.**

### Örnek

$$
A=(2,4)
$$

$$
B=(8,10)
$$

olsun.

$$
M=
\left(
\frac{2+8}{2},
\frac{4+10}{2}
\right)
$$

$$
\boxed{M=(5,7)}
$$

---

# 5. Kartezyen Koordinat Sisteminde Vektör

Vektör yalnızca bir noktanın konumunu değil, **büyüklük + yön** bilgisini ifade eder.

Bir vektörü ok ile gösterebiliriz:

$$
\vec A
$$

Bir vektörün:

* başlangıç noktası
* bitiş noktası
* büyüklüğü
* yönü

vardır.

Örneğin:

```text
          B
          ●
         ↗
        ↗
       ↗  A
      ●
      A
```

Burada ok:

$$
A\rightarrow B
$$

yönünde ilerler.

---

# 6. İki Noktadan Vektör Bulmak

Başlangıç noktası:

$$
A=(x_1,y_1)
$$

Bitiş noktası:

$$
B=(x_2,y_2)
$$

ise:

$$
\boxed{
\vec{AB}
=
(x_2-x_1,\ y_2-y_1)
}
$$

Burada mantık:

$$
\boxed{\text{bitiş noktası}-\text{başlangıç noktası}}
$$

şeklindedir.

### Örnek

$$
A=(2,3)
$$

$$
B=(7,5)
$$

ise:

$$
\vec{AB}
=
(7-2,\ 5-3)
$$

$$
\boxed{\vec{AB}=(5,2)}
$$

Bu şu anlama gelir:

* x yönünde `5`
* y yönünde `2`

ilerlemiştir.

---

# 7. Vektörün Bileşenleri

Bir vektörü x ve y yönlerindeki iki parçaya ayırabiliriz.

$$
\boxed{
\vec A=A_x\hat i+A_y\hat j
}
$$

Burada:

* \(A_x\) → x bileşeni
* \(A_y\) → y bileşeni
* \(\hat i\) → x yönündeki birim vektör
* \(\hat j\) → y yönündeki birim vektör

Örneğin:

$$
\vec A=3\hat i+4\hat j
$$

demek:

$$
A_x=3
$$

$$
A_y=4
$$

demektir.

---

# 8. Birim Vektörler

**Birim vektör**, büyüklüğü `1` olan ve yalnızca yön belirtmek için kullanılan vektördür.

Kartezyen sistemde:

$$
\boxed{\hat i}
$$

x yönünü,

$$
\boxed{\hat j}
$$

y yönünü gösterir.

Üç boyutta ayrıca:

$$
\boxed{\hat k}
$$

z yönünü gösterir.

Dolayısıyla:

$$
\boxed{
\vec A=A_x\hat i+A_y\hat j
}
$$

ve üç boyutta:

$$
\boxed{
\vec A=A_x\hat i+A_y\hat j+A_z\hat k
}
$$

---

# 9. Vektörün Büyüklüğü

Bir vektör:

$$
\vec A=(A_x,A_y)
$$

şeklindeyse büyüklüğü Pisagor teoremiyle bulunur:

$$
\boxed{
|\vec A|=\sqrt{A_x^2+A_y^2}
}
$$

### Örnek

$$
\vec A=(3,4)
$$

ise:

$$
|\vec A|
=
\sqrt{3^2+4^2}
$$

$$
=\sqrt{9+16}
$$

$$
\boxed{|\vec A|=5}
$$

Bu, `3-4-5` dik üçgenidir.

---

# 10. Vektörün Yönü

Bir vektörün x ekseniyle yaptığı açıya:

$$
\boxed{\theta}
$$

diyelim.

Dik üçgenden:

$$
\tan\theta=\frac{A_y}{A_x}
$$

Dolayısıyla:

$$
\boxed{
\theta=\tan^{-1}
\left(
\frac{A_y}{A_x}
\right)
}
$$

Ancak burada çok önemli bir ayrıntı vardır:

> [!warning]
> Sadece `tan⁻¹(Ay/Ax)` hesaplamak **her zaman yeterli değildir**.
>
> Vektörün hangi bölgede olduğunu kontrol etmelisin.
>
> Çünkü x ve y'nin işaretleri açının hangi quadrant'ta olduğunu belirler.

Örneğin:

$$
A_x<0,\quad A_y>0
$$

ise vektör II. bölgededir.

---

# 11. Kutupsal (Polar) Koordinat Sistemi

Kartezyen sistemde bir nokta:

$$
\boxed{(x,y)}
$$

ile gösterilir.

Kutupsal sistemde ise:

$$
\boxed{(r,\theta)}
$$

ile gösterilir.

Burada:

* \(r\) → orijinden noktaya olan uzaklık
* \(\theta\) → pozitif x ekseninden itibaren ölçülen açı

şeklindedir.

```text
              y
              ↑
              |
              |       ● P
              |      /
              |     / r
              |    /
              | θ /
--------------+----------------→ x
            (0,0)
```

Kartezyen:

$$
(x,y)
$$

Kutupsal:

$$
(r,\theta)
$$

aynı noktayı farklı biçimlerde tanımlar.

---

# 12. Kartezyen → Kutupsal Dönüşüm

Elimizde:

$$
P=(x,y)
$$

olsun.

Önce \(r\)'yi buluruz.

Pisagor:

$$
r^2=x^2+y^2
$$

Dolayısıyla:

$$
\boxed{
r=\sqrt{x^2+y^2}
}
$$

Sonra açıyı buluruz:

$$
\tan\theta=\frac{y}{x}
$$

$$
\boxed{
\theta=\tan^{-1}
\left(
\frac{y}{x}
\right)
}
$$

Fakat tekrar:

> [!important]
> \(\theta\)'yı bulurken **quadrant kontrolü** yapılmalıdır.

---

## Örnek

Noktamız:

$$
P=(3,4)
$$

olsun.

### 1. r

$$
r=\sqrt{3^2+4^2}
$$

$$
r=5
$$

### 2. θ

$$
\theta=
\tan^{-1}
\left(
\frac43
\right)
$$

$$
\theta\approx53.13^\circ
$$

Dolayısıyla:

$$
\boxed{
P=(5,\ 53.13^\circ)
}
$$

kutupsal koordinatlarda aynı noktayı gösterir.

---

# 13. Kutupsal → Kartezyen Dönüşüm

Bu kez elimizde:

$$
(r,\theta)
$$

var.

Dik üçgenden:

$$
\cos\theta=\frac{x}{r}
$$

buradan:

$$
\boxed{x=r\cos\theta}
$$

Benzer şekilde:

$$
\sin\theta=\frac{y}{r}
$$

buradan:

$$
\boxed{y=r\sin\theta}
$$

Dolayısıyla:

$$
\boxed{
(r,\theta)
\rightarrow
(x,y)
}
$$

dönüşümü:

$$
\boxed{x=r\cos\theta}
$$

$$
\boxed{y=r\sin\theta}
$$

ile yapılır.

---

# 14. Kartezyen ↔ Kutupsal Formül Özeti

> [!important] EZBERLE

### Kartezyen → Kutupsal

$$
\boxed{
r=\sqrt{x^2+y^2}
}
$$

$$
\boxed{
\theta=\tan^{-1}\left(\frac{y}{x}\right)
}
$$

### Kutupsal → Kartezyen

$$
\boxed{
x=r\cos\theta
}
$$

$$
\boxed{
y=r\sin\theta
}
$$

Bunlar konunun en önemli formülleridir.

---

# 15. Derece ve Radyan

Açılar iki farklı şekilde ifade edilebilir:

* derece: `°`
* radyan: `rad`

Temel dönüşüm:

$$
\boxed{180^\circ=\pi\ rad}
$$

Dolayısıyla:

$$
\boxed{
\theta_{\text{rad}}
=
\theta_{\text{derece}}
\frac{\pi}{180}
}
$$

Örneğin:

$$
90^\circ=\frac{\pi}{2}
$$

$$
180^\circ=\pi
$$

$$
270^\circ=\frac{3\pi}{2}
$$

$$
360^\circ=2\pi
$$

---

# 16. Quadrantlar ve Açıların İşaretleri

Bir noktanın x ve y koordinatlarının işaretleri bulunduğu bölgeyi belirler.

| Bölge |  x |  y | Açının aralığı                |
| ----- | -: | -: | ----------------------------- |
| I     |  + |  + | \(0^\circ\) – \(90^\circ\)    |
| II    |  - |  + | \(90^\circ\) – \(180^\circ\)  |
| III   |  - |  - | \(180^\circ\) – \(270^\circ\) |
| IV    |  + |  - | \(270^\circ\) – \(360^\circ\) |

Bu nedenle:

$$
\theta=\tan^{-1}(y/x)
$$

hesaplandıktan sonra sonucu **quadrant ile kontrol etmek gerekir**.

---

# 17. Vektörün Polar Gösterimi

Bir vektör de kutupsal biçimde ifade edilebilir.

Örneğin:

$$
\boxed{
\vec A=(A,\theta)
}
$$

burada:

* \(A\) → vektörün büyüklüğü
* \(\theta\) → yön açısı

Kartezyen gösterimi ise:

$$
\boxed{
\vec A=A_x\hat i+A_y\hat j
}
$$

şeklindedir.

Aralarındaki dönüşüm:

$$
A_x=A\cos\theta
$$

$$
A_y=A\sin\theta
$$

---

# 18. Vektör Toplama

İki vektör:

$$
\vec A=A_x\hat i+A_y\hat j
$$

$$
\vec B=B_x\hat i+B_y\hat j
$$

olsun.

Toplam:

$$
\vec R=\vec A+\vec B
$$

olur.

Bileşenleri ayrı ayrı toplarız:

$$
\boxed{
R_x=A_x+B_x
}
$$

$$
\boxed{
R_y=A_y+B_y
}
$$

Dolayısıyla:

$$
\boxed{
\vec R=(A_x+B_x)\hat i+(A_y+B_y)\hat j
}
$$

---

## Örnek

$$
\vec A=(3,4)
$$

$$
\vec B=(2,-1)
$$

ise:

$$
\vec R=\vec A+\vec B
$$

$$
R_x=3+2=5
$$

$$
R_y=4+(-1)=3
$$

Dolayısıyla:

$$
\boxed{\vec R=(5,3)}
$$

Büyüklüğü:

$$
|\vec R|
=
\sqrt{5^2+3^2}
=
\sqrt{34}
$$

---

# 19. Vektör Çıkarma

Vektör çıkarma:

$$
\boxed{
\vec A-\vec B
=
\vec A+(-\vec B)
}
$$

şeklinde düşünülebilir.

Yani:

$$
\vec B=(B_x,B_y)
$$

ise:

$$
-\vec B=(-B_x,-B_y)
$$

olur.

Dolayısıyla:

$$
\boxed{
\vec A-\vec B
=
(A_x-B_x,\ A_y-B_y)
}
$$

---

# 20. Negatif Vektör

Bir vektörün negatifini almak:

* büyüklüğünü değiştirmez
* yönünü 180° tersine çevirir.

Örneğin:

$$
\vec A=(3,4)
$$

ise:

$$
\boxed{-\vec A=(-3,-4)}
$$

ve:

$$
|\vec A|=|-\vec A|
$$

olur.

---

# 21. Vektörlerin Geometrik Toplanması

Vektörler geometrik olarak da toplanabilir.

**Uçtan uca yöntemi:**

1. İlk vektörü çiz.
2. İkinci vektörün başlangıcını ilk vektörün ucuna taşı.
3. İlk vektörün başlangıcından son vektörün ucuna çizilen ok, sonuç vektörüdür.

```text
A: ─────→

         B: ─────→

Sonuç:

A başlangıcı ─────────────→ sonuç
```

Ancak fizik problemlerinde analitik yöntem genellikle daha kullanışlıdır:

$$
x\text{ bileşenlerini topla}
$$

$$
y\text{ bileşenlerini topla}
$$

Sonra gerekirse:

$$
R=\sqrt{R_x^2+R_y^2}
$$

ile büyüklüğü bul.

---

# 22. Vektörlerde Başlangıç Noktası Önemli mi?

Bir vektörün **konumu** değil, büyüklüğü ve yönü önemlidir.

Örneğin:

$$
\vec A=(3,4)
$$

ve başka bir yerde çizilmiş:

$$
\vec B=(3,4)
$$

aynı büyüklük ve yöne sahipse eşit vektörlerdir:

$$
\boxed{\vec A=\vec B}
$$

Bu nedenle vektörler düzlem üzerinde paralel olarak taşınabilir.

> [!note]
> Bu özellik **serbest vektör** fikrinin temelidir.

---

# 23. Konum Vektörü

Orijinden bir noktaya çizilen vektöre **konum vektörü** denir.

Nokta:

$$
P=(x,y)
$$

ise konum vektörü:

$$
\boxed{
\vec r=x\hat i+y\hat j
}
$$

şeklindedir.

Örneğin:

$$
P=(3,4)
$$

için:

$$
\boxed{
\vec r=3\hat i+4\hat j
}
$$

ve büyüklüğü:

$$
|\vec r|=5
$$

olur.

Bu nedenle bir noktanın Kartezyen koordinatları ile orijinden o noktaya giden konum vektörünün bileşenleri arasında doğrudan ilişki vardır.

---

# 24. İki Boyuttan Üç Boyuta

Fizikte daha ileride üç boyutlu koordinat sistemi kullanacağız.

Bu durumda:

$$
(x,y,z)
$$

olur.

Üç eksen:

* x
* y
* z

ve üç birim vektör:

$$
\hat i,\hat j,\hat k
$$

vardır.

Bir vektör:

$$
\boxed{
\vec A=A_x\hat i+A_y\hat j+A_z\hat k
}
$$

şeklinde yazılır.

Büyüklüğü:

$$
\boxed{
|\vec A|
=
\sqrt{
A_x^2+A_y^2+A_z^2
}
}
$$

olur.

---

# 25. Konunun Büyük Resmi

Bu dersin aslında birbirine bağlı birkaç aşaması var:

```text
KOORDİNAT SİSTEMİ
       ↓
Bir noktanın konumunu ifade et
       ↓
VEKTÖR
       ↓
Büyüklük + yön
       ↓
BİLEŞENLER
       ↓
x ve y yönlerine ayır
       ↓
KARTEZYEN ↔ KUTUPSAL
       ↓
Farklı gösterimler arasında dönüşüm
       ↓
VEKTÖR İŞLEMLERİ
       ↓
Toplama / çıkarma
       ↓
Fizik problemlerinde kullan
```

---

# 26. Sınavlık Formül Listesi

> [!important] ⭐ EZBERLENMESİ GEREKENLER

## İki nokta arasındaki uzaklık

$$
\boxed{
d=\sqrt{(x_2-x_1)^2+(y_2-y_1)^2}
}
$$

## Orta nokta

$$
\boxed{
M=
\left(
\frac{x_1+x_2}{2},
\frac{y_1+y_2}{2}
\right)
}
$$

## İki noktadan vektör

$$
\boxed{
\vec{AB}=(x_B-x_A,\ y_B-y_A)
}
$$

## Vektörün büyüklüğü

$$
\boxed{
|\vec A|=\sqrt{A_x^2+A_y^2}
}
$$

## Vektörün yönü

$$
\boxed{
\theta=\tan^{-1}\left(\frac{A_y}{A_x}\right)
}
$$

> Quadrant kontrolünü unutma.

## Polar → Kartezyen

$$
\boxed{
x=r\cos\theta
}
$$

$$
\boxed{
y=r\sin\theta
}
$$

## Kartezyen → Polar

$$
\boxed{
r=\sqrt{x^2+y^2}
}
$$

$$
\boxed{
\theta=\tan^{-1}\left(\frac{y}{x}\right)
}
$$

## Vektör bileşen gösterimi

$$
\boxed{
\vec A=A_x\hat i+A_y\hat j
}
$$

## Vektör toplama

$$
\boxed{
\vec A+\vec B
=
(A_x+B_x)\hat i+(A_y+B_y)\hat j
}
$$

## Vektör çıkarma

$$
\boxed{
\vec A-\vec B
=
(A_x-B_x)\hat i+(A_y-B_y)\hat j
}
$$

## Derece-radyan

$$
\boxed{
180^\circ=\pi\ rad
}
$$

---

# 27. En Çok Karıştırılabilecek Noktalar

### 1. Nokta ve vektör aynı şey değildir

Nokta:

$$
\boxed{P=(x,y)}
$$

Vektör:

$$
\boxed{\vec A=A_x\hat i+A_y\hat j}
$$

---

### 2. Orta nokta ile vektör aynı formül değildir

Orta nokta:

$$
\left(
\frac{x_1+x_2}{2},
\frac{y_1+y_2}{2}
\right)
$$

Vektör:

$$
(x_2-x_1,y_2-y_1)
$$

Biri **iki noktanın ortasını**, diğeri **bir noktadan diğerine olan yönlü değişimi** bulur.

---

### 3. Polar koordinatta ilk sayı uzaklıktır

$$
(r,\theta)
$$

ifadesinde:

* `r` → uzaklık
* `θ` → açı

---

### 4. cos → x, sin → y

Açı pozitif x ekseninden ölçülüyorsa:

$$
\boxed{x=r\cos\theta}
$$

$$
\boxed{y=r\sin\theta}
$$

---

### 5. Negatif bileşen yönü gösterir

$$
A_x<0
$$

ise vektörün x bileşeni **-x yönündedir**.

$$
A_y<0
$$

ise y bileşeni **-y yönündedir**.

Bu nedenle vektör bileşenleri negatif olabilir.

---

# 28. Mini Örnek — Tüm Konuyu Birleştirelim

Bir nokta:

$$
P=(3,4)
$$

olsun.

### Kartezyen koordinatları

$$
\boxed{(3,4)}
$$

### Orijinden uzaklığı

$$
r=\sqrt{3^2+4^2}
$$

$$
\boxed{r=5}
$$

### Açısı

$$
\theta=\tan^{-1}\left(\frac43\right)
$$

$$
\boxed{\theta\approx53.13^\circ}
$$

### Polar koordinatları

$$
\boxed{(5,53.13^\circ)}
$$

### Konum vektörü

$$
\boxed{
\vec r=3\hat i+4\hat j
}
$$

### Vektörün büyüklüğü

$$
\boxed{|\vec r|=5}
$$

### Tersine dönüşüm

$$
x=5\cos(53.13^\circ)\approx3
$$

$$
y=5\sin(53.13^\circ)\approx4
$$

Yani tekrar:

$$
\boxed{(x,y)=(3,4)}
$$

elde edilir.

---

# 29. Bu Dersten Çıkarken Bilmem Gerekenler

Bu konunun sonunda şunları yapabiliyor olmalıyım:

* [ ] Kartezyen koordinat sisteminde nokta gösterebilmek
* [ ] Bir noktanın hangi quadrant'ta olduğunu belirleyebilmek
* [ ] İki nokta arasındaki uzaklığı bulabilmek
* [ ] İki noktanın orta noktasını bulabilmek
* [ ] İki noktadan bir vektör oluşturabilmek
* [ ] Bir vektörü x ve y bileşenlerine ayırabilmek
* [ ] Vektörün büyüklüğünü bulabilmek
* [ ] Vektörün yön açısını bulabilmek
* [ ] Kutupsal koordinat sistemini anlayabilmek
* [ ] Kartezyen → kutupsal dönüşüm yapabilmek
* [ ] Kutupsal → Kartezyen dönüşüm yapabilmek
* [ ] Derece ↔ radyan dönüşümü yapabilmek
* [ ] Vektörleri bileşenleri üzerinden toplayabilmek
* [ ] Vektörleri bileşenleri üzerinden çıkarabilmek
* [ ] \(\hat i,\hat j,\hat k\) birim vektörlerini anlayabilmek
* [ ] Bir noktanın konum vektörünü yazabilmek

---

> [!tip] Dersin ana fikri
> **Koordinat sistemi bize "nerede?" sorusunun, vektör ise "ne kadar ve hangi yönde?" sorusunun cevabını verir.**
>
> Kartezyen sistemde konumu:
>
> $$
> (x,y)
> $$
>
> şeklinde ifade ederiz.
>
> Kutupsal sistemde aynı konumu:
>
> $$
> (r,\theta)
> $$
>
> şeklinde ifade ederiz.
>
> Aralarındaki bağlantıyı sağlayan temel matematik ise **Pisagor + sinüs + kosinüs + tanjant**tır.

