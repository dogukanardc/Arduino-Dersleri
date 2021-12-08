#Ders-1

Merhabalar,

Arduino Derslerinin 1. Bölümüne hoşgeldiniz.

Bu bölümde yapacaklarımız:<br />
  1)Arduino Nedir? Ne işe yarar? Nerede kullanabilir?<br />
  2)Komponentler nedir? Arduino ile Nasıl kullanılır ?<br />
  3)Giriş seçenekleri / bağlantıları / pinleri<br />
  4)Kart programlama araçları<br />
  5)Kod döngüleri<br />
  6)Kütüphane yönetimi<br />
  7)Nasıl Kodlanır?<br />
 
### 1)Arduino Nedir? Ne işe yarar? Nerede kullanabilir?<br />
  Arduino okullar için oluşturulan dünyadaki en ünlü Maker kartlarından biridir. Bu kart basit olmakla beraber çok fazla kullanım alanına sahiptir. Elektroniğe başlangıç yapacak kişilerin elektroniğin temellerini anlaması açısından gereklidir. Belirli komponentler ile geliştirmeye açık ve açık kaynak kodlamaya sahip bir karttır.<br />
  Birçoook kullanım alanına sahiptir, **sonuçta her yiğidin yoğurt yiyişi farklıdır**. Kafanızdaki projeye göre kullanım amaçları şekillenmektedir. Zaten zaman ile fark edeceksiniz ki bir süre sonra arduino size yetmeyecek ve daha performanslı bir kart arayışına girişeceksiniz. Bir ipucu vereyim karşınıza ilk çıkacak kart Raspberry pi (Eğitimini vermek için önce biz tam olarak öğrenmemiz gerekecek :D )
  
### 2)Komponentler nedir? Arduino ile Nasıl kullanılır ?<br />
  Birçok komponent var aslında, her projeye göre de değişiklik gösteriyor. Varsayalım ki robot kol yapmak istiyorsunuz ee o zaman tekerlekle işiniz olmaz ki :) Bu nedenden ötürü projeyi kafanızda tasarlarken aklınızda hemen hangi komponentle daha iyi yapabilirim diye şekillenecektir.<br /> 
  Bizde bulunan komponentleri kısaca açıklayayım sizlere:<br /><br />
  -**HCSR04 Ultasonik Mesafe sensörü:** Ses dalgalarını kullanarak mesafe ölçmeye yarayan modül. (DI DIIIT yanlış cevap kendisi ölçüp al abim/ablam mesafe budur demiyor. mesafeyi de siz hesaplayacaksınız burada her şey manuel...)<br />
  -**DC-Motor:** Gerilimi ve akımı arttırdıkça belirli bir yönde dönen motorlardır.<br />
  -**L298N Motor sürücü:** Motorların sürülmesi için gerekli olan akımı ve RPM'i ayarlayan sürücü devresidir. Bizi büyük yükten kurtarır. Motor sürücüye vereceğimiz komutlarla motoru çooook rahat sürmemizi sağlar. Motorun tüm velinimetlerinden yararlanmamıza da olanak tanır.<br />
  -**SG90 RC Mini Servo Motor:** Belirlediğiniz açıda dönen motordur.<br />
  -**Breadboard:** Türkçesi ekmek tahtası olsa da tüm bağlantıları önce buraya yaparız. (Biz maker'lar için ekmek tahtasıdır ya aslında :D)<br />
  -**Jumper Kablo:** Komponentleri bağlayan tatlı mı tatlı kablolardır.<br />
  -**LED:** Yanar.<br />
  -**Potansiyometre:** Analog giriş vermermizi sağlar. 0-255 arası değer gönderir.<br />
  -**Buzzer:** DÜT-DÜÜÜTTT diye öterr.<br />
  -**Direnç:** Siz mühendis olduğunuz için açıklamama gerek yok bence :D<br />
  -**Buton:** Arduinoya dijital (lojik) değer gönderir. Küçüktür ama çok işe yarar.<br />

### 3)Giriş seçenekleri / bağlantıları / pinleri:<br />
  Arduinoda baya fazla Dijital giriş/çıkış var 13 tane civarı. 5 Tane de analog giriş/çıkışı mevcut.
  
### 4)Kart programlama araçları<br />:
  Arduino'nun hazırlamış olduğu Arduino IDE programını kullancağız ki güzel sade tatlı bir programdır. Çoook işimize yarayacaktır. Sadece arduino için değil bakmayın adı arduino olduğuna birçok kartı programlar.
  

Arduino klon:
![](Uno-Klon.jpg)


asd
def
<br />*01010011 01101001 01100110 01110010 01100101 00111010 00100000 01010100 01001110 01001011 01010101 01010010 01000001 01010011*
