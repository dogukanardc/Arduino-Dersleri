# Ders-2

Merhabalar, 
Arduino Derslerinin 2. Bölümüne hoşgeldiniz.

Bu bölümde yapacaklarımız:<br />
  1)Değişkenler<br />
  1)Matematiksel işlemler<br />
  2)Operatörler (if/else/while/for)<br />
  3)Serial Monitör Nedir? Ne işe yarar?<br />
  4)Led Yakma<br />
  5)Ledi Breadboard üzerinde Yakma<br />
  
### 1)Değişkenler:<br/>
  Değişkenler bir algoritmanın olmazsa olmazıdır. Birçok projede trilyonlarca bile bulunabilir mesela elinizdeki cep telefonlarının ekran ışığı bile 0-100 arasında bir değişkene bağlı bu değişkenle birlikte ekran arkası paneller bu sayıya göre ışık seviyesini yükseltip düşürür. Kısaca işimize yarayacak değişken yani veriable'lardan kısaca bahsedeyim size:<br/><br/>
     **- int:** Integer açılımı olan bir değişken türü 2 byte yani 16 bitlik veri atayabilirsiniz.<br/>
     **- bool:** Doğru veya yanlış depolar sadece veya 1,0 oda zaten doğru yanlışa tekabul ediyor.<br/>
     **- char:** 1 bytelık veri depolar 0-255 arasında veri saklayabilirsiniz.<br/>
    **- unsigned int:** Git gide büyüyor işler :) burada da 0-65535 arasında veri atayabilirsiniz.<br/>
    **- long:** Vuhuuuu milyonlar başlasın o zaman... 32 bitlik veri depolarsınız yaniii -2 milyonla +2 milyon arasında veri demek (maşallah)<br/>
    **- float:** Buda baya büyüktür ama iş ondalıktır. Yani 3.65846 tarzı sayılar depolarsınız.<br/>
    **- string:** Sonunda yazıya geçebildik. Buda sayı depolar. Sınırsızdır.<br/><br/>
    
Hadi bir örnek veri vereyim.<br/>
    
```C
int sayi = 12345;
```
  
tarzında gibi... Sondaki noktalı virgülü unutmayın. Valla kodunuz falan çalışmaz sonra bana kod bozuk falan demeyin :)<br/>
      
### 2)Matematiksel işlemler:<br />
  Öncelikle matematiksel işlemler normal işlemlerle aynı :) 9 + 4 vb. ama her şeyden önce veriable yani değişken tanımlamak gerekiyor. Değişkenleri diğer maddede bahsedeceğim. Değişkene istediğimiz şeyleri tanımlayıp daha sonrasında da onları kullanmak arduino da basittir ve çok işinize yarar.

### 2)Operatörler (if/else/while/for)<br />
  **İF:** Bu öperatör aslında en önemli kod öperatörüdür. Derslerde görülen kapıların  tam karşılık manasını anlamamıza olanak sağlar aslında. Belirli bir değeri karşılaştırır ve o değer dediğiniz şeye eşitse o zaman size içinde bulunan kodun kullanım hakkına erişme imkanı sunar örnek hemen aşağıda:
 <br />
 
```C
int sayi = 12345;

if (sayi == 12345){
  Serial.println("Sayiniz 12345");
  }
```

  **ELSE:** Bu öperatör if'in tam tersidir Ya değilse? demektir. Yani yukarıdaki biçime örnek verecek olursak: <br />
  
```C
int sayi = 12345;

if (sayi == 12345){
  Serial.println("Sayiniz 12345");
  }
else{
  Serial.println("Kankam Sayın 12345 Değil")
  }
```

  **While:** İçindeki işlem gerçekleşene kadar kodu döndürüp durur. Mesela wifi'a bağlanmak için sistem bağlanana kadar tekrar tekrar dener. gibi :). Örneği hemen aşağıda...
  <br />
  
```C
  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  } 
 ```
 <br />
 Burada sistem wifi ağına bağlanmak için deniyor da deniyor ve seri monitöre . (nokta) koyuyor. İşte web siteleri veya uygulamalarda bulunan yükleniyor kısmı buradan geliyor:)
 <br />
  **For:** Buda içindeki değerin oluşturulmasını bekler. Örnek Aşağıda:
   <br />
  
```C
 for (int i = 0; i <= 255; i++) {
    analogWrite(PWMpin, i);
    delay(10);
  } 
 ```
 <br />
 Burada doktor elimizde bulunan bir servo motoru 0 'dan 255. adıma kadar yükseltmesini anlatmaya çalışıyor. 
 <br />
 
 
### 3)Serial Monitör Nedir? Ne işe yarar?<br />
  Çok basit. Yukarıdaki örneklerden de az biraz anladığınız kadarıyla aslında bizim arduino içinde ne olup bittiğini anlamamıza sağlayan bir kapı. Arduinoya kabloyla bağlı olduğumuz sürece Arduino IDE yazılımı üzerinden monitörden içerideki şeyleri takip edebiliriz. Tabi içeride ne olup bittiğini siz tanımlayacaksınız. (Şu an şunu yapıyorum, gibi).<br />
Belirli şeyler var aslında o kodlar serial monitör başlamak ve bitirmek için en önem arz eden kısımlarından. Alalım sizi aşağıya:
     <br />
  
```C
Serial.begin(9600); // Pc'ye 9600 frekans genişliğinde bağlan.
Serial.println("Selam Dünya"); //Pc'ye mesaj gönder.
  } 
 ```

  
 
