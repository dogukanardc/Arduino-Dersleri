# Ders-2

Merhabalar, 
Arduino Derslerinin 2. Bölümüne hoşgeldiniz. Bu dersimizde hiç olmadığımız kadar LED ile uğraşacağız. Umarım elinizde bir tane yoktur yakmamaya dikkat edin :D

Bu bölümde yapacaklarımız:<br />
  1)Değişkenler<br />
  1)Matematiksel işlemler<br />
  2)Operatörler (if/else/while/for)<br />
  3)Serial Monitör Nedir? Ne işe yarar?<br />
  4)Led Yakma<br />
  5)Ledi Breadboard üzerinde Yakma<br />
  6)Buton ile Led yakma<br />
  7)LDR sensörü ile Kendi kendine açılan LED yapımı<br />
  8)RGB Led Kullanımı<br />
  9)Potansiyometre ile Değer okumak<br />
  10)HCSR-04 Ultrasonik Mesafe Sensörü nedir?<br />
  11)Park sensörü yapımı<br />
  
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
 ```

<br /> Seri monitör penceresinde çıkan sonuçlar Serial.println("Selam Dünya"); Kısmında yazdığınız Selam Dünya kısmı yazılır.<br />

### 4)Led Yakma<br />
 Led yakmak Arduino için neler yapılabileceğimiz konusunda en önemli kısımlarındandır aslında. Önce onboard led yakmayı daha sonrasında ise kablo ve breadboard ile yakmaktan bahsedeceğim. Kodu ve Bağlantılarını aşağıda bulabilirsin.
 <br />
 **Bağlantıları:** <br />
<img src="https://github.com/dogukanardc/Arduino-Dersleri/blob/main/Ders%232%20-%20Arduino%20Uygulamalar%C4%B1na%20Giri%C5%9F/onboard.png" alt="sensör" width="300"/><br />

**Kod:** <br />
(İsterseniz Dosya>Örnekler>Basics>Blink olarak da seçebilirsiniz.) <br />

```C
void setup() {
  // Led'i Çıkış olarak gosteriyoruz. BUILTIN-LED varsayılan olarak 13 numaralı dijital pine baglıdır.
  pinMode(LED_BUILTIN, OUTPUT);
}

// Sonsuza kadar giden döngümüz.
void loop() {
  digitalWrite(LED_BUILTIN, HIGH);   // Ledi YAK (HIGH yani yuksek voltaj degeri.)
  delay(1000);                       // 1 saniye bekle (milisaniye cinsinden belirtilmiştir.)
  digitalWrite(LED_BUILTIN, LOW);    // Ledi SONDUR voltajı dusuk yaparak
  delay(1000);                       // 1 saniye bekle
}
 ```
<br />

### 5)Ledi Breadboard üzerinde Yakma<br />
Tıpatıp aynıdır aslında ama tek fark vardır, öncesinde LED pinini belirtmeniz gerekmektedir ve kablo çekmeniz gerekmektedir. Arduinomuzun 8. Dijital pinimize ledin + bacağını bağlıyoruz. Eksiler her zaman GND ye gider unutmayın. Normalde direnç kullanmamız gerekli uzun kullanım için ve ledi yakmamak (gerçekten yakmamak için fire anlamında yani) ama şimdilik bağlantıyı bu şekilde yapmamız işimizi görecektir. Kodu ve Bağlantılarını aşağıya bıraktım :)<br />

**Bağlantıları:** <br />
<img src="https://github.com/dogukanardc/Arduino-Dersleri/blob/main/Ders%232%20-%20Arduino%20Uygulamalar%C4%B1na%20Giri%C5%9F/breadboard.png" alt="sensör" width="600"/><br /><br />
<br />
**Kod:** <br />
(İsterseniz Dosya>Örnekler>Basics>Blink olarak da seçip değeri 8 ile değiştirebilirsiniz.) <br />

```C
void setup() {
  // 8 Numaralı dijital çıkışı arduinomuza tanıtıyoruz.
  pinMode(8, OUTPUT);
}

// Sonsuza kadar giden döngümüz.
void loop() {
  digitalWrite(8, HIGH);   // Ledi YAK (HIGH yani yuksek voltaj degeri.)
  delay(1000);                       // 1 saniye bekle (milisaniye cinsinden belirtilmiştir.)
  digitalWrite(8, LOW);    // Ledi SONDUR voltajı dusuk yaparak
  delay(1000);                       // 1 saniye bekle
}
 ```
 <br />
 
### 6)Buton ile Led yakma<br />
Evveeett geldik fiziksel olarak kontrol edebileceğimiz şeylere yaniii buton ile led yakma uygulamasına hemen ihtiyacımız olan şeyleri yazıyorum:<br />
*Led<br />
*Buton<br />
*Arduino<br />
*Jumper Kablo<br />
*Ennn önemlisi de dersi verecek olan bir Doğukan :)<br />
<br />
* Hadi projenin bağlantılarını ve kodlarını paylaşayım size:<br />

