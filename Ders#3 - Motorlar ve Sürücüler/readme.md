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
  <img src="https://github.com/dogukanardc/Arduino-Dersleri/blob/main/Ders%232%20-%20Arduino%20Uygulamalar%C4%B1na%20Giri%C5%9F/breadboard.png" alt="sensör" width="600"/><br /><br />
  
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
  <img src="https://github.com/dogukanardc/Arduino-Dersleri/blob/main/Ders%232%20-%20Arduino%20Uygulamalar%C4%B1na%20Giri%C5%9F/breadboard.png" alt="sensör" width="600"/><br /><br />
  *Soket Besleme:* Soketle beslemek arduino üzerinde modem girişlerine benzer bir güç girişi var (yuvarlak olan he işte o). O girişten 9V luk bir giriş bağladığımızda güzel bir besleme elde edebiliyoruz.
  <img src="https://github.com/dogukanardc/Arduino-Dersleri/blob/main/Ders%232%20-%20Arduino%20Uygulamalar%C4%B1na%20Giri%C5%9F/breadboard.png" alt="sensör" width="600"/><br /><br />
  



