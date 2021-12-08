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
  -**HCSR04 Ultasonik Mesafe sensörü:** Ses dalgalarını kullanarak mesafe ölçmeye yarayan modül. (DI DIIIT yanlış cevap kendisi ölçüp al abim/ablam mesafe budur demiyor. mesafeyi de siz hesaplayacaksınız burada her şey manuel...)
  -**DC-Motor:** Gerilimi ve akımı arttırdıkça belirli bir yönde dönen motorlardır.
  -**L298N Motor sürücü:** Motorların sürülmesi için gerekli olan akımı ve RPM'i ayarlayan sürücü devresidir. Bizi büyük yükten kurtarır. Motor sürücüye vereceğimiz komutlarla motoru çooook rahat sürmemizi sağlar. Motorun tüm velinimetlerinden yararlanmamıza da olanak tanır.
  -**SG90 RC Mini Servo Motor:** Belirlediğiniz açıda dönen motordur.
  -**Breadboard:** Türkçesi ekmek tahtası olsa da tüm bağlantıları önce buraya yaparız. (Biz maker'lar için ekmek tahtasıdır ya aslında :D)
  -**Jumper Kablo:** Komponentleri bağlayan tatlı mı tatlı kablolardır.
  -**LED:** Yanar.
  -**Potansiyometre:** Analog giriş vermermizi sağlar. 0-255 arası değer gönderir.
  -**Buzzer:** DÜT-DÜÜÜTTT diye öterr.
  -**Direnç:** Siz mühendis olduğunuz için açıklamama gerek yok bence :D
  -**Buton:** Arduinoya dijital (lojik) değer gönderir. Küçüktür ama çok işe yarar.


Arduino klon:
![](Uno-Klon.jpg)


asd
def
