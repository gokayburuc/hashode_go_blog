## STRUCT IFADESI NEDIR? 

### GİRİŞ

Yazıya ait kodlama ve tanımlamalara geçmeden önce bir LO-FI müzik paylaşalım. Yazıyı okurken play tuşuna basarak müziği başlatmanızı  ve yazıyı bu şekilde okumanızı tavsiye ederim.

%[https://soundcloud.com/lofi_girl/after-all?utm_source=clipboard&utm_medium=text&utm_campaign=social_sharing]

### TANIM 

> Struct ifadesi verileri belirli formlarda gruplandırmak için oluşturulan alan koleksiyonlarıdır.Oluşturacağımız kayıtları daha önceden belirlenmiş bir veri şablonununa dayalı olacak şekilde düzenli olarak tutmaya yarar. 

### NE İŞE YARAR ? 

1. Veri yapılarını toplu olarak tanımlamak için elverişlidirler. 
2. Verileri gruplamak için kullanışlıdır.
3. Defalarca çağırılabilirler. 

### STRUCT IFADESİ ÖRNEĞİ

Bir örnek üzerinden anlatırsam aklınızda daha iyi yer edebileceğini düşünüyorum.

```go
package main

import (
	"fmt"
)

type veriler struct {
	fiyat         float64
	depo          float64
	yakit_tuketim float64
	mesafe        float64
}

type doviz struct {
	usd_try_price float64
	eur_try_price float64
	rub_try_price float64
	bgn_try_price float64
	gbp_try_price float64
}

func main() {

	var benzin veriler

	benzin.fiyat = 29.35
	benzin.yakit_tuketim = 5.5
	benzin.depo = 40
	benzin.mesafe = 350

	var doviz_fiyat doviz
	doviz_fiyat.usd_try_price = 16.75
	doviz_fiyat.eur_try_price = 17.28
	doviz_fiyat.rub_try_price = 0.31
	doviz_fiyat.bgn_try_price = 8.98
	doviz_fiyat.gbp_try_price = 20.41

	fmt.Println("\n")
	fmt.Println("Kilometre Tüketim Fiyatları")
	fmt.Println("====================================================")
	fmt.Println("Kilometre Yakıt (LT):", "\t", benzin.yakit_tuketim/100)
	fmt.Println("Kilometre Fiyatı (TRY):\t", (benzin.yakit_tuketim/100)*benzin.fiyat)

	fmt.Println("\n")
	fmt.Println("Fiyatlar")
	fmt.Println("====================================================")

	fmt.Println("Fiyat (TRY):\t", benzin.fiyat)
	fmt.Println("Fiyat (USD):\t", benzin.fiyat/doviz_fiyat.usd_try_price)
	fmt.Println("Fiyat (EUR):\t", benzin.fiyat/doviz_fiyat.eur_try_price)
	fmt.Println("Fiyat (RUB):\t", benzin.fiyat/doviz_fiyat.rub_try_price)
	fmt.Println("Fiyat (GBP):\t", benzin.fiyat/doviz_fiyat.gbp_try_price)
}

```


Yukarıdaki örnekte ilk olarak bir struct ifadesi tanımladık. Struct ifadelerinin yazım şekli aşağıda verilmiştir: 

```go

type structname struct{
    variable  string
    variable2 float32
    variable3 int
    variable4 bool
    ...
}

```

Struct ifademizi tanımladıktan sonra ikinci aşamada fonksiyon içinde kullanışımıza geçiyoruz. Onun da yazımı aşağıdaki şekildedir. 

```go
//ilk olarak degisken tanimlanir ve bu degiskenin hangi struct ifadesindeki sablona uyacagı belirlenir.
var variablename structname

//yeni tanımlanan degisken variablename üzerinde mevcut sablondaki formatlara göre atamalar yapılır.
variablename.variable1 = "isim"
variablename.variable2 = 35.0
variablename.variable3 = 29
variablename.variable4 = false

```

Bizim ilk verdiğimiz benzin fiyatı hesaplama CLI Scriptine geri dönersek, ilk olarak verilerimizin hangi formda yazılacağını struct ifadesi ile tanımladık. Bundan sonrasında kullanacağımız ifadeleri tanımlama kısımları daha kolay olacaktır. Bunu tetristeki formlar gibi düşünebiliriz.

![Tetris](https://media.giphy.com/media/MOSebUr4rvZS0/giphy.gif)

`veriler` ismiyle tanımladığımız struct ifadesine dayanarak `benzin` isimli bir degisken tanimladik. Bu degisken altinda noktadan sonra ifade edilecek olan `property` ifadeleri ( `benzin.fiyat` ifadesi örnek olarak alınabilir ) daha once tanımladığımız `veriler` isimli **struct** ifademize bağlı olacaktır. Yani `benzin.fiyat` ifadesi **struct** ifademizde tanımladığımız `fiyat` ifadesi gibi yalnızca `float64` ifade degerini alabilir.



### AÇIKLAMA

```go
	var benzin veriler

	benzin.fiyat = 29.35
	benzin.yakit_tuketim = 5.5
	benzin.depo = 40
	benzin.mesafe = 350

	var doviz_fiyat doviz

	doviz_fiyat.usd_try_price = 16.75
	doviz_fiyat.eur_try_price = 17.28
	doviz_fiyat.rub_try_price = 0.31
	doviz_fiyat.bgn_try_price = 8.98
	doviz_fiyat.gbp_try_price = 20.41

```

`veriler` isimli **struct** ifadesinde tanımladığımız değerlere ait değişkenler `benzin` ismiyle yer almaktadır. Değer atamaları yapılmıştır.

`doviz` isimli **struct** ifadesinde tanımladığımız değerler ise `doviz_fiyat` isimli degiskene atanmıştır. 
Burada günlük döviz kurları belirtilmiştir. 


```go
	fmt.Println("\n")
	fmt.Println("Kilometre Tüketim Fiyatları")
	fmt.Println("====================================================")
	fmt.Println("Kilometre Yakıt (LT):", "\t", benzin.yakit_tuketim/100)
	fmt.Println("Kilometre Fiyatı (TRY):\t", (benzin.yakit_tuketim/100)*benzin.fiyat)

	fmt.Println("\n")
	fmt.Println("Fiyatlar")
	fmt.Println("====================================================")

	fmt.Println("Fiyat (TRY):\t", benzin.fiyat)
	fmt.Println("Fiyat (USD):\t", benzin.fiyat/doviz_fiyat.usd_try_price)
	fmt.Println("Fiyat (EUR):\t", benzin.fiyat/doviz_fiyat.eur_try_price)
	fmt.Println("Fiyat (RUB):\t", benzin.fiyat/doviz_fiyat.rub_try_price)
	fmt.Println("Fiyat (GBP):\t", benzin.fiyat/doviz_fiyat.gbp_try_price)
```

Degiskenler ile hesaplama islemleri yapıldıktan sonra ekrana yazdırılmıştır. Kod çalıştırıldıktan sonra sonuçlar ekrana yazdırılmıştır.


### KODUN ÇALIŞTIRILMASI 

Kodumuzu `benzin.go` ifadesi olarak kaydedip aşağıdaki kod ile çalıştırıdığımızda resimdeki çıktıyı verecektir. 

```bash
go run benzin.go
```

![code.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656339984970/KSWywmxpU.png align="left")




--------------------------------------


## İÇ İÇE STRUCT İFADELERİ 

Buraya kadar tek bir struct ifadesinin tanımlanmasını ve  değer atamasını anlattık. Peki `instance` olarak geçen yani iç içe geçmiş bir struct ifadesi nasıl yazılır? Buyrun örneğimize geçelim.

```go



package main
 
import "fmt"
 
type rectangle struct {
	length  int
	breadth int
	color   string
 
	geometry struct {
		area      int
		perimeter int
	}
}
 
func main() {
	var rect rectangle // dot notation
	rect.length = 10
	rect.breadth = 20
	rect.color = "Green"
 
	rect.geometry.area = rect.length * rect.breadth
	rect.geometry.perimeter = 2 * (rect.length + rect.breadth)
 
	fmt.Println(rect)
	fmt.Println("Area:\t", rect.geometry.area)
	fmt.Println("Perimeter:", rect.geometry.perimeter)
}

```
Burada kodu dikkatle incelediğinizde ilk işlemden farklı olarak struct tanımlamasına şu şekilde başladık.

```go

type rectangle struct {
    length  int
    breadth int
    color   string

    geometry struct {
        area      int
        perimeter int
    }
}

```

İkinci defa struct ifadesi azarken type ile başlamadık ve bu ifadeyi ilk struct ifadesine ait olan süslü parantez `{}` içinde yazdık. Yani `rectangle` isimli struct ifadesinin alt struct ifadesi `geometry` ifadesidir. Bu şu anlama gelir; 

> `geometry` isimli struct ifadesine ait degişkenler `rectangle` struct ifadesinin bir alt kümesidir.



Şimdi `main()` fonksiyonu içerisine bakarak biraz detaya inelim. 

```go
func main() {
	var rect rectangle // dot notation
	rect.length = 10
	rect.breadth = 20
	rect.color = "Green"
 
	rect.geometry.area = rect.length * rect.breadth
	rect.geometry.perimeter = 2 * (rect.length + rect.breadth)
 
	fmt.Println(rect)
	fmt.Println("Area:\t", rect.geometry.area)
	fmt.Println("Perimeter:", rect.geometry.perimeter)
}

```

Burada tanımladığımız `rect.length` bildiğimizi bir struct ifadesidir. Fakat `rect.geometry.area` isimli bir değişken tanımladık. Burada **polymorphism** kavramına değinmek gerekiyor. 


> **POLIMORFIZM** *(Çok -Şekillilik bknz. Yunanca)***:** Programlama dili teorisinde ve tip teorisinde, polimorfizm, farklı türlerdeki varlıklara tek bir arabirimin sağlanması veya birden çok farklı türü temsil etmek için tek bir sembolün kullanılmasıdır.

Yani buradaki işlemimizde `rectange` struct ifadesi ve onun miras ifadesi olan `geometry` ifadesi ile **polimorfizm ** de ifade edildiği üzere tek bir ana ifade ile birden çok şekli tanımlıyoruz.


Fonksiyonumuzun son kısmında yer alan `fmt.Println("Perimeter:", rect.geometry.perimeter)` ifadesi içinde de net olarak `rect.geometry.perimeter` ifadesini görüyoruz. `perimeter` isimli degisken `geometry` isimli struct'a, bu struct ta `rect` isimli struct degisken ifadesine bağlıdır. 

### SONUÇ

Bu yazımda struct ifadelerinden kısaca bahsetmeye çalıştım.
