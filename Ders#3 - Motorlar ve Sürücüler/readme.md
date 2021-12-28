Merhabalar, Arduino dersinin 3. kısmına hoşgeldin. Bu bölümde motorlar ve sürücüler hakkında uzun uzadıya uğraşacağız. Gerekli komponentlerden, robotun çalışması için gerekli şeylerden güç kaynaklarından bahsedeceğim ve son olarak da yarışma duyurusunda bulunacağım.<br /><br />

Bu bölümde yapacaklarımız:<br />
  1)Park Sensörü Uygulaması<br />
  2)Güç Kontrolü ve Sistemleri (Piller ve değerleri)
  3)DC Motor Nedir ? Nasıl çalışır ?<br />
  4)Step Motor Nedir ? Nasıl çalışır ?<br />
  5)Servo Motor Nedir ? Nasıl çalışır ?<br />
  6)L298N Motor sürücü Nedir ? Nasıl çalışır ?<br />
  7)DC Motor sürme (L298N ile)<br /> 
  8)Servo Motor Kontrolü<br />
  9)Yarışma duyursu ve tanıtımı<br />
  
 
### 1)Park Sensörü Uygulaması<br />
  Park sensörü uygulaması aslında mesafe ölçümü kadar kolay ve zahmetsiz. Ekstra olarak bize buzzer gerekiyor ki park sensörünün ana mantığını işleyebilelim. Hadi Başlayalım:<br />
  **Bağlantıları:**<br />
  <img src="https://github.com/dogukanardc/Arduino-Dersleri/blob/main/Ders%233%20-%20Motorlar%20ve%20S%C3%BCr%C3%BCc%C3%BCler/parksensoru.jpg" alt="sensör" width="600"/><br /><br />
  
  **KOD:**<br />
  
```C
const int trigger_pin = 12; //12. pini trigger pin olarak tanımlandı.
const int echo_pin = 13; //13. pini echo pin olarak tanımlandı.
int uyariLed = 2; //2. pini uyariLed olarak tanımlandı.
int buzzer = 6; //6. pini buzzer olarak tanımlandı.

int sure ; //sure adlı bir değişken tanımlandı.
int mesafe ; //mesafe adlı bir değişken tanımlandı.

void setup() {

pinMode(uyariLed , OUTPUT); //aled'i çıkış olarak tanımladık.
pinMode(buzzer , OUTPUT); //buzzer'i çıkış olarak tanımladık.
pinMode(trigger_pin , OUTPUT); //trigger pin'i çıkış olarak tanımladık.
pinMode(echo_pin , INPUT); //echo pin'i giriş olarak tanımladık.

}

void loop()
{
digitalWrite(trigger_pin , HIGH);
delayMicroseconds(1000);
digitalWrite(trigger_pin , LOW);
sure = pulseIn(echo_pin , HIGH); //echo_pin verisi sure değişkenine atandı.
mesafe = (sure / 2) / 29.1; //cm cinsine çevrildi.
if (mesafe <= 10) //mesafe 10 cm den kısaysa aşağdaki işlemler gerçekleşir.
{
digitalWrite(uyariLed , HIGH);
digitalWrite(buzzer , HIGH);
}
else if(mesafe>10 && mesafe<=20) //Mesafe 10 cm den uzun 20cm de eşit veya kısaysa aşağdaki işlemler gerçekleşir.
{
digitalWrite(uyariLed , HIGH);
digitalWrite(buzzer , HIGH);
delay(150); // ledin yanık kalma süresiyle buzzerin uyarı süresi standart bir süreye 150ms ye ayarlandı.
digitalWrite(uyariLed , LOW);
digitalWrite(buzzer , LOW);
delay(250);
}
else if(mesafe>20 && mesafe<=30) //Mesafe 20 cm den uzun 30cm de eşit veya kısaysa aşağdaki işlemler gerçekleşir.
{
digitalWrite(uyariLed , HIGH);
digitalWrite(buzzer , HIGH);
delay(150);
digitalWrite(uyariLed , LOW);
digitalWrite(buzzer , LOW);
delay(450);
}
else if(mesafe>30 && mesafe<=40) //Mesafe 30 cm den uzun 40cm de eşit veya kısaysa aşağdaki işlemler gerçekleşir.
{
digitalWrite(uyariLed , HIGH);
digitalWrite(buzzer , HIGH);
delay(150);
digitalWrite(uyariLed , LOW);
digitalWrite(buzzer , LOW);
delay(650);
}
else if(mesafe>40 && mesafe<=50) //Mesafe 40 cm den uzun 50cm de eşit veya kısaysa aşağdaki işlemler gerçekleşir.
{
digitalWrite(uyariLed , HIGH);
digitalWrite(buzzer , HIGH);
delay(150);
digitalWrite(uyariLed , LOW);
digitalWrite(buzzer , LOW);
delay(850);
}
}
```
  
<br /><br />

### 2)Güç Kontrolü ve Sistemleri (Piller ve değerleri)<br />
  Aslında her şey DC akım kullanarak normal bir şekilde besleniyor. Arduino 5V 1A lik akıma ihtiaç duyuyor (oda maximum yani) ve beslemek için 2 faklı kaynağa ihtiyacımız olabilir:<br />
  *USB kablo ile:* Kablo ile bağlantıda hem bilgisayardan veri aktarımı yapabiliyoruz hemde gücü bilgisayardan çekebiliyoruz (Bilgisayarın verebildiği kadar tabi)<br />
  *Dışarıdan Besleme:* Birçok yolu var aslında ya pille yada sabit güçle besleyebiliriz. Fakat burdaki sıkıntı Arduino üzerindeki VIN girişi ve GND girişlerini kullanmalıyız. İstediğinizi takabilirsiniz. Yeterki 9V girişi Geçmeyin yakarsınız aman diyim :) <br />
  <img src="https://github.com/dogukanardc/Arduino-Dersleri/blob/main/Ders%233%20-%20Motorlar%20ve%20S%C3%BCr%C3%BCc%C3%BCler/VinPin.webp" alt="sensör" width="600"/><br /><br />
  *Soket Besleme:* Soketle beslemek arduino üzerinde modem girişlerine benzer bir güç girişi var (yuvarlak olan he işte o). O girişten 9V luk bir giriş bağladığımızda güzel bir besleme elde edebiliyoruz.<br />
  <img src="https://github.com/dogukanardc/Arduino-Dersleri/blob/main/Ders%233%20-%20Motorlar%20ve%20S%C3%BCr%C3%BCc%C3%BCler/barrel_jack.webp" alt="sensör" width="600"/><br /><br /><br />
  
### 3)DC Motor Nedir ? Nasıl çalışır ?<br />
  DC motor yani direkt akım motoru adındaki bu motor çok basit bir mantıkla çalışır aslında İki ucundaki potansiyellerin farklılığından doğan manyetik gücü kullanarak içerisindeki bobinlere itme kuvveti uygular bu sayede de bilin bakalım ne olur? DÖNER.<br />
  <img src="https://github.com/dogukanardc/Arduino-Dersleri/blob/main/Ders%233%20-%20Motorlar%20ve%20S%C3%BCr%C3%BCc%C3%BCler/dc.gif" alt="sensör" width="600"/><br /><br /><br /><br />

### 4)Step Motor Nedir ? Nasıl çalışır ?<br />
  DC motorun birazdaha komplike versiyonudur yani bu motorda her bir adım için bir kez elektrik vermek gerekir. Sıra sıra elektrik verilir bu sayede step motor yani adım motoru bir adım atar. İnce işlerde ve gerçekten tutma bırakma tarzında belli kordinatlara eksiksiz gitmesini istediğiniz projeleri step motor kullanarak gerçekleştirebilirsiniz.<br />
  <img src="https://github.com/dogukanardc/Arduino-Dersleri/blob/main/Ders%233%20-%20Motorlar%20ve%20S%C3%BCr%C3%BCc%C3%BCler/step.gif" alt="sensör" width="600"/><br /><br /><br /><br />
  
### 5)Servo Motor Nedir ? Nasıl çalışır ?<br />
  İçinde potansiyometre bulunan bir DC motordur. Fakat buradaki olay içinde potansiyometre bulunduğundan dolayı sadece 180 derece ile sınırlıdır. Step sınırsız döner. Servo motorda adım atmazsınız direkt o konuma döndürürsünüz motoru. Mesela; 60 Dereceye dön gibi. (derecede dön değil. o dereceye dön. yani motor 60 derece olunca durucuak kendini orada tutuacak.)
   <img src="https://github.com/dogukanardc/Arduino-Dersleri/blob/main/Ders%233%20-%20Motorlar%20ve%20S%C3%BCr%C3%BCc%C3%BCler/servo.gif" alt="sensör" width="600"/><br /><br /><br /><br />
  
### 6)L298N Motor sürücü Nedir ? Nasıl çalışır ?<br />
  En çok kullandığım motor sürücüdür. Adı üstünde motoru sürer.<br />
  <img src="https://github.com/dogukanardc/Arduino-Dersleri/blob/main/Ders%233%20-%20Motorlar%20ve%20S%C3%BCr%C3%BCc%C3%BCler/l298n.jpg" alt="sensör" width="600"/><br />
  
  Bu kadar kısa bitirmeyecem sandınız dimi :D Bu motor sürücü aynı anda 2 DC motor sürebilir veya 1 tane step motor sürebilir. Servoda sürdüğü olur ama hiç L298N dahil edip masraf şişirmeye gerek yok onu arduino da sürer :) (kısa olmayacak dedim sanki kısa oldu biraz. dur birazdaha uzatayım...) Farklı olarak ENABLE pinleri var bu kartta yani bir motoru aktif veya deaktif edebiliyorsunuz ve güç tasarrufu sağlayabiliyorsunuz :) (Yeter bence çokta uzatmıyım :D )<br /><br />
 
 #### 7)DC Motor sürme (L298N ile)<br /> 
  Evvet anlattık anlattık şimdi sırada DC motor sürme var. Kitin içindeki dc motorların ister birini ister ikisini de sürebilirsiniz seçim sizin :)
  
**Bağlantıları:**<br />
  <img src="https://github.com/dogukanardc/Arduino-Dersleri/blob/main/Ders%233%20-%20Motorlar%20ve%20S%C3%BCr%C3%BCc%C3%BCler/dcsurme.jpg" alt="sensör" width="600"/><br /><br />
  
  **KOD:**<br />
  
```C
const int Enable_A = 9;
const int Enable_B = 10;
const int inputA1 = 2;
const int inputA2 = 3;
const int inputB1 = 4;
const int inputB2 = 5;

void setup()
{
pinMode(Enable_A, OUTPUT);
pinMode(Enable_B, OUTPUT);
pinMode(inputA1, OUTPUT);
pinMode(inputA2, OUTPUT);
pinMode(inputB1, OUTPUT);
pinMode(inputB2, OUTPUT);
}
void loop()
{
//---- A ve B Cikis olarak etkinlestir------//
digitalWrite(Enable_A, HIGH);
digitalWrite(Enable_B, HIGH);
//----------Run motors-----------//
digitalWrite(inputA1, HIGH);
digitalWrite(inputA2, LOW);
digitalWrite(inputB1 , HIGH);
digitalWrite(inputB2, LOW);
delay(3000);
//-------motoru devre disi birak----------//
digitalWrite(Enable_A, LOW);
digitalWrite(Enable_B, LOW);
delay(3000);
//-------Ters Bağlama----------//
digitalWrite(Enable_A, HIGH);
digitalWrite(Enable_B, HIGH);
digitalWrite(inputA1, LOW);
digitalWrite(inputA2, HIGH);
digitalWrite(inputB1 , LOW);
digitalWrite(inputB2, HIGH);
delay(3000);
//-------Motor devre disi----------//
digitalWrite(Enable_A, LOW);
digitalWrite(Enable_B, LOW);
delay(3000);
//----------Hiz yukselt----------//
for(int i = 0; i &lt; 256; i++)
{
analogWrite(Enable_A, i);
analogWrite(Enable_B, i);
delay(40);
}
//----------Hiz dusur----------//
for(int j = 256; j &gt; 0; j--)
{
analogWrite(Enable_A, j);
analogWrite(Enable_B, j);
delay(40);
}
//-------motoru devre dışı bırak----------//
digitalWrite(Enable_A, LOW);
digitalWrite(Enable_B, LOW);
delay(3000);
}
```

<br /><br />

### 8)Servo Motor Kontrolü<br />
 Evvet Servo motor çok tatlı bir motor dimi. Ama biraz kanser (öğrenene kadar öğrendikten sonra her şeyi onunla yapmak isteyeceksiniz valla bak) Şimdi sürmesini göstericem.<br />
 **Bağlantıları:**<br />
  <img src="https://github.com/dogukanardc/Arduino-Dersleri/blob/main/Ders%233%20-%20Motorlar%20ve%20S%C3%BCr%C3%BCc%C3%BCler/servobaglanti.jpg" alt="sensör" width="600"/><br /><br />
  
  
  ***KODA BAŞLAMADAN ÖNCE!!!!!!!*** Servo.h kütüphanesini indirmeniz gerekmektedir. Nasıl indireceğimizi aşağıda göstereceğim. Dikkatle yapın. <br />
  
  <img src="https://github.com/dogukanardc/Arduino-Dersleri/blob/main/Ders%233%20-%20Motorlar%20ve%20S%C3%BCr%C3%BCc%C3%BCler/kutuphane1.png" alt="sensör" width="600"/><br />
  <img src="https://github.com/dogukanardc/Arduino-Dersleri/blob/main/Ders%233%20-%20Motorlar%20ve%20S%C3%BCr%C3%BCc%C3%BCler/kutuphane2.jpg" alt="sensör" width="600"/><br />
  
  **KOD:**<br />
  
```C
#include <Servo.h>  // Servo kütüphanesini projemize ekledik.
Servo servoM;  // Servo nesnemizi oluşturduk, ismini servoM yaptık.
int pos = 0;    // pos değişkenini oluşturup 0’a eşitledik.
void setup() {
  servoM.attach(9);  // Servoyu 9nolu pin’e bağladığımızı belirttik.
}
void loop() {
  for (pos = 0; pos <= 180; pos += 1) { // For döngüsü ile 0 ile 180 derece arası gitmesini sağladık.
                                        // her bir adımda 1 derece artacak şekilde ayarladık.
    servoM.write(pos);              // Servo açı değeri olarak belirlediğimiz pos değişkenini servoya yazdırdık.
    delay(15);                       // servonun hedeflenen açıya gidebilmesi için 15 ms bekleme ekledik.
  }
  for (pos = 180; pos >= 0; pos -= 1) { // for döngüsü ile 180 ile 0 derece arası gitmesini sağladık.
    servoM.write(pos);              // Servo açı değeri olan pos değişkenini servo’ya yazdırdık.
    delay(15);                       // Servonun açı değerine gidebilmesi için 15 ms. bekleme ekledik.
  }
}
```

<br /><br />
 
### 9)Yarışma duyursu ve tanıtımı<br />
  Dersten önce bahsetmeyelim :) Deste parkurun çizimini ve temsili bir robotu size tanıtacağız buna göre neredeyse 1 hafta süreniz olacak. Daha sonrasında derste yarışma yapıp eğer eksikleri varsa robotunuzu inceleyeceğiz. Eksik kısımları nasıl egale edebilirsiniz anlatacağız. <br /><br />
  
  Bugünlük dersimiz bu kadardı. Teşekkür eder iyi günler dilerim.<br />
  
  -Doğukan ARDIÇ
