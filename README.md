# BEM (Block Element Modifier)

## Temiz Kod Ankayışı;

İyi yazılımcı güzel temiz kod yazan yazılımcıdır. Bir koda verilen önem kodun temizliğinden, yalınlığından anlaşılabildiği gibi yazan yazılımcımında işine verdiği değeri yansıtır aynı zamanda. Unutulmaması gereken nokta, yazılım bir sanattır ve sanatçısı yazılımcıdır :)

“Sonra asla demektir”
  
Bir kod yazılırken asla daha sonra temize çekerim diye başlanmamalı. Sonra temize çekme asla olmayacaktır. Çünkü;
Kod biriktikçe yönetilebilrliği azalacak, karmaşık ve anlamsız hale gelecektir.

##### Kod karmaşasının sonuçları;
> Takımların verimliliği düşer ve sıfıra yaklaşır. Verimlilik düştükçe de yöneticiler yapabildikleri tek şeyi yaparlar; verimliliği artırması umudu ile projeye daha çok insan kaynağı eklerler. Takımdaki herkes verimliliği artırmak için büyük baskı altındadır. Öyle ki verimliliği sıfıra daha da yaklaştıracak şekilde kod karmaşası yaratmaya devam ederler.

##### İyi kod nasıl kötü koda dönüşür;
> İyi bir kodun kötü koda dönüşmesinin bir çok nedeni vardır. En büyük nedenlarinden biride, maalesef profesyonel davranmamamız. Kodlarımızı günübirlik düşünüp, esnek, pratik düşünmüyoruz. Genelde günü kurtarmaya yönelik çalıştığımız için projeler ilerledikçe tıkanmakta ve kodun yönetimi zorlaşmaktadır.

#### Temiz kod için neler yapmalıyız?

"Temiz kod her zaman ona değer veren biri tarafından yazılmış gibi görünür."

- Bir kod yazılmadan önce parçalar ayrı ayrı düşünülmeli. Her bir parça sonradan kullanılabilir şekilde, mantıklı genel isimlendirmeler verilmeli.
- Gereksiz yorumlarda, kodlardan ve amaç dışında kullanımlardan uzak durulmalı.
- Program veya uygulamanın isterlerine göre uygun ölçekte pozitif parça ve parçacıklardan oluşmalı.
- İlişkili teknoloji ve dillere uygun, rahat yorumlanıp, okunulabilir bir yapıyla proje iskeleti oluşturulup geliştirmeye hazır olmalı.
- İş ortamında iletişim iyi düzeyde tutulup, gerekli durumlarda proje ile ilgili takım içi iletişimden çekinmemeli. 

Unutulmaması gerekir, temiz kod arayışında olmak iyi yazılımcı olmak için atılacak en büyük adım olur.


## BEM Nedir ?

BEM (Block Element Modifier) bir css metadolojisidir. Yandex Tarafından geliştirilmiş, bir stil adlandırma kuralıdır.

BEM ile doğru, stabil ve belli bir standart isimlendirmeler amaçlanmaktadır. Kodun okunulabilir olması için oldukça önemli bir yer almaktadır.

#### Peki nedir bu Block Element Modifier ;
#### Block;
> Genelde birden fazla elementi kapsayan büyük yapılardır. Bloklar kendi içlerinde birden fazla item'ı grup olarak içinde barındırır. Kendi içinde blocklar bulundurabilirler. Oluşturduğumuz componentler, widgetlar veya global tanımlı her bir anlamlı parçalar birer block parçası olabilir ve block olarak tanımlanabilir.

 ![Alt text](https://miro.medium.com/max/1257/1*eFlkVoLUdAy8eSJXPBBG6Q.png?raw=true "Title")
 
Yukarıdaki Twitter home page örneğinde, sayfanın mantıklı bloklara ayrılış biçimi kırmısı borderlar ile görünmektedir. Her bir parça bir BEM bloğunu temsil etektedir. Örnekteki bloklar Header, side-left, side-right, ve main gibi isimlendirilebilir.

![Alt text](https://miro.medium.com/max/1206/1*xUMPgcFYsL53DEK7CgdOsQ.png?raw=true "Title")

Yukardaki görüntüde header bloğununda kendi içinde üç ara bloğa bölündüünü görebiliriz.
 
  ![Alt text](https://miro.medium.com/max/140/1*ZApq-kqz0s-G7xmn2cu0Zg.png?raw=false "Title")
   .header bloğu içindeki .logo bloğu
   
    
Genel olarak örneklere Header bloğu ile devam edeceğiz.

```
  <header class="header">
      ///HTML5 semantic element'i olan header'a ".header" class'ı verilerek bloğumuzu oluşturmuş olduk.
  </header>
  
```

```
<!-- HTML -->
  <header class="header">
    <nav class="nav">
      ///Burda Blok içinde blok ypmış olduk.
    </nav>
  </header>
  
<!-- HTML -->

.nav {
  ....
}


```

#### Element
> Element'ler temelde block'lar içinde olan ` blok elemanlarıdır `. 

  ![Alt text](https://miro.medium.com/max/378/1*4htCS_T0z8RAIQzl68qlKQ.png?raw=false "Title")
    .header bloğu içindeki .search bloğu
    
```
<div class="block">
  <div class="block__element">
    //content
  </div>
</div>

```
Search Bloğu ;

```
<!-- HTML -->
<header class="header">
  <div class="search">
     <input class="search__input" type="text" name="search" placeholder="Search Twitter">
     <img class="search__profile-img" src="../../profile.png">
     <button class="search__button" type="button">Tweet</button>
  </div>
</header>
  
<!-- CSS (less veya sass ile birlikte) -->

.search {
  ...
  
  &__input {
    ...
  }
  &__profile--img {
    ...
  }
  &__button {
    ...
  }
}
   
```


### Modifier
 Block elemanına ek stiller kullanmak için oluşturulur.
 
  ![Alt text](https://miro.medium.com/max/378/1*ynf3eybGhZXs-1F-l_3AdQ.png?raw=false "Title")
    .header bloğu içindeki .search bloğu
 
 ```
 <!-- HTML -->
 <header class="header">
  <div class="search">
     <input class="search__input" type="text" name="search" placeholder="Search Twitter">
     <img class="search__profile-img" src="../../profile.png">
     <button class="search__button search__button--error" type="button">Tweet</button>
  </div>
</header>

<!-- CSS (less veya sass ile birlikte) -->

.search {
  ...
  
  &__input {
    ...
    
    &--error {
      ...
    }
  }
}
   
 
 ```
 
 
#### BEM Örnek UI Örneği;

![Alt text](image/code-rev-1.jpg?raw=false "Title")

    
    
  
    
   


