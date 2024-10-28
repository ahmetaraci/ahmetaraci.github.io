---
title: Windows Terminal'de En Çok Kullanılan Komutlar
date: 18/10/2024 11:00:00 +0300
categories: [Türkçe, Rehber]
tags: [Windows, Terminal]
---

Windows Terminal, geliştiriciler ve ileri düzey kullanıcılar için vazgeçilmez bir araçtır. Bu blog yazısında, Windows Terminal'de en sık kullanılan komutları ve bu komutların nasıl kullanıldığını detaylı bir şekilde ele alacağız.

#### 1. `dir` Komutu

Dosya ve dizinlerin listesini görüntülemek için kullanılır.

```sh
  dir
```

Komutun çıktısı buna benzer görünecektir.

```plaintext
C:\Users\KullaniciAdi> dir
Açık olan klasör: C:\Users\KullaniciAdi

Tarih                Saat        Boyut      Ad
---------------------------------------------------
10/19/2024  10:00 AM             <DIR>      Belgeler
10/19/2024  10:00 AM             <DIR>      Resimler
10/19/2024  10:00 AM             <DIR>      Müzik
10/19/2024  10:00 AM             <DIR>      Videolar
10/19/2024  10:00 AM             <DIR>      Masaüstü
10/19/2024  10:00 AM       1,024,000  Dosya.txt
               5 dosya(lar)      1,024,000 byte
               5 klasör(ler)  5,000,000,000 byte
```

#### 2. `cd ` Komutu

- Bir üst dizine geçmek:

  ```sh
  cd ..
  ```

- Belirli bir dizine gitmek:

  ```sh
  cd C:\Users\KullanıcıAdı\Belgeler
  ```

- Bir Dizin İçindeki Alt Dizin:

  ```sh
  cd AltDizinAdı
  ```

- Eğer dizin adında boşluk varsa, dizin adını tırnak içinde yazmalısınız:

  ```sh
  cd "C:\Kullanıcılar\Kullanıcı Adı\Belgeler"
  ```

#### 3. `mkdir` ve `rmdir` Komutları

Yeni bir dizin oluşturmak ve bir dizini silmek için kullanılır.

- Yeni bir dizin oluşturmak:

  ```sh
  mkdir YeniKlasor
  ```

Bu komut içinde bulunan dizin içinde `YeniKlasor` isimli bir dizin oluşturur.

- Birden Fazla Dizin Oluşturma:

  ```sh
  mkdir Dizin1 Dizin2 Dizin3
  ```

Bu komut, mevcut dizinde "Dizin1", "Dizin2" ve "Dizin3" adlı üç dizin oluşturur.

- Bir dizini silmek (dizin boş olmalıdır):

  ```sh
  rmdir YeniKlasor
  ```

- İçi dolu bir dizini silmek için:

  ```sh
  rmdir /s YeniKlasor
  ```

- Dizini Onaylama Olmadan Silme: Eğer silme işlemini onay istemeden yapmak isterseniz, /q (quiet) seçeneğini ekleyebilirsiniz:

  ```sh
  rmdir /s /q YeniKlasor
  ```

Komutu sade `/s` parametresiyle verirsek dizin içerisi dolu olduğu durumda bizden onay isteyecektir.

#### 4. `copy` Komutu

Kopyalama yapmak için copy komutu kullanır. Temel olarak `copy [kaynak] [hedef]`

- Basit dosya kopyalama :
  ```sh
  copy C:\Kullanıcılar\KullanıcıAdı\Belgeler\dosya.txt D:\Yedekler\
  ```

Bu komut, "dosya.txt" dosyasını "D:\Yedekler" dizinine kopyalar.

- Farklı İsimle Kopyalama:

  ```sh
  copy C:\Kullanıcılar\KullanıcıAdı\Belgeler\dosya.txt C:\Kullanıcılar\KullanıcıAdı\Masaüstü\yeni_dosya.txt
  ```

Bu komut, "dosya.txt" dosyasını "Masaüstü"ne "yeni_dosya.txt" adıyla kopyalar.

- Birden Fazla Dosya Kopyalama: Eğer birden fazla dosya kopyalamak isterseniz, dosya adlarını belirtmelisiniz. Örneğin:

  ```sh
  copy C:\Kullanıcılar\KullanıcıAdı\Belgeler\*.txt D:\Yedekler\
  ```

Bu komut, "Belgeler" dizinindeki tüm `.txt` dosyalarını "D:\Yedekler" dizinine kopyalar.

#### 5. `move` Komutu

Taşıma yapmak için move komutu kullanır. Temel olarak `move [kaynak] [hedef]`

- Tek Dosya Taşıma:

  ```sh
  move C:\Dosyalar\belge.txt D:\YeniKlasor\
  ```

  Bu komut, `C:\Dosyalar` klasöründeki `belge.txt` dosyasını `D:\YeniKlasor` klasörüne taşır.

- Birden Fazla Dosya Taşıma:

  ```sh
  move C:\Dosyalar\*.txt D:\YeniKlasor\
  ```

  Bu komut, `C:\Dosyalar` klasöründeki tüm `.txt` dosyalarını `D:\YeniKlasor` klasörüne taşır.

- Dizin Taşıma:

  ```sh
  move C:\EskiKlasor D:\YeniKlasor\
  ```

  Bu komut, `C:\EskiKlasor` dizinini `D:\YeniKlasor` dizinine taşır.

  #### 5.1 `move` Komutunun Ek Parametreleri

  - **/Y:** Var olan dosyaların üzerine yazmak için onay istemez.
  - **/-Y:** Var olan dosyaların üzerine yazmadan önce onay ister.

#### 6. `del` Komutu

`del` komutu ile klasörleri silemeyiz sadece dosyaları silebiliriz. Klasör silmek için yukarıda bahsettiğimiz `rmdir` komutu kullanılır. `del` komutu ile silinen dosyalar geri döndürülemez.

- Tek Bir Dosya Silme:
  ```sh
  del C:\Dosyalar\belge.txt
  ```
- Birden Fazla Dosya Silme:

  ```sh
  del C:\Dosyalar\*.txt
  ```

  Bu komut, `C:\Dosyalar` klasöründeki tüm `.txt` uzantılı dosyaları siler.

- Alt Dizindeki Tüm Dosyaları Silme:

  ```sh
  del C:\Dosyalar\* /S
  ```

  Bu komut, `C:\Dosyalar` klasöründeki tüm dosyaları ve alt dizinlerdeki tüm dosyaları siler.

  #### 6.1 `move` Komutunun Ek Parametleri

  - **/P**: Her dosya silinmeden önce onay ister.
  - **/F**: Sadece salt okunur dosyaları siler.
  - **/S**: Alt dizinlerdeki dosyaları da siler.
  - **/Q**: Sessiz modda çalışır; dosyaları silerken onay istemez.

#### 7. `cls` veya `clear` Komutu

`clear` komutu aslında unix tabanlı işletim sistemlerinin terminallerinde kullanılır ancak Windows PowerShell de çalışır. `clear` ve `cls` komutları terminal ekranındaki herşeyi temizlemeye yarar.

- **Önemli** : `clear`_komutu cmd'de çalışmaz, sadece PowerShell üzerinde çalışır._

  ```sh
  clear
  ```

  ```sh
  cls
  ```

#### 8. `echo` Komutu

`echo` komutu ekranda metin göstermek veya bir scriptin içerisindeki değişken değerlerini göstermek için kullanılır.

- Basit Metin Yazdırma:

  ```sh
  echo O zaman bağırın ulan FENERBAHÇE ÇOK YAŞA diye!
  ```

- Değişken Yazdırma: Örneğin, bir çevresel değişkeni yazdırmak için:

  ```sh
  echo %USERPROFILE%
  ```

  Çıktısı şuna benzeyecektir.

  ```sh
  C:\Users\KullaniciAdi
  ```

- Boş Bir Satır Yazdırma:

  ```sh
  echo.
  ```

  Bu komut, ekranınıza bir boş satır ekler. Yani, önceki çıktılar ile yeni komut arasında bir boşluk oluşturmuş olursunuz.

#### 9. `type` Komutu

`type` komutu metin tipindeki dosyaları hızlıca incelemek için çok faydalıdır.

- Tek Bir Dosyanın İçeriğini Görütüleme:

  ```sh
  type C:\Dosyalar\belge.txt
  ```

- Birden Fazla Dosyanın İçeriğini Görüntüleme:

  ```sh
  type C:\Dosyalar\dosya1.txt C:\Dosyalar\dosya2.txt
  ```

- **Büyük Dosyalar**: _Eğer dosya çok büyükse, type komutu çıktıyı ekrana tıpkı bir akış gibi yazdırır. Bu, dosya içeriğinin ekranda kaybolmasına neden olabilir. Bu durumda more komutunu kullanarak sayfa sayfa görüntüleme yapabilirsiniz:_
  ```sh
  type C:\Dosyalar\büyük_dosya.txt | more
  ```
- **Dosya Türleri**: _type komutu yalnızca metin dosyaları için uygundur. İkili dosyalar veya diğer formatlardaki dosyalar için kullanıldığında anlamlı bir çıktı vermez._

  **Özetle** `type` komutu, metin dosyalarının içeriğini görüntülemek için kullanışlı bir araçtır ve basit bir metin okuma işlemi için idealdir. Eğer dosyalarınız çok büyükse veya içeriği daha kontrollü bir şekilde görüntülemek isterseniz, more komutunu da düşünebilirsiniz.

#### 10. `tasklist` ve `taskkill` Komutları

`tasklist` komutu çalışan processleri görüntüler. Processlerin PID lerinede ulaşılır.

- Tüm Processleri Listeleme :

  ```sh
  tasklist
  ```

- Belirli Bir Uygulamanın Sürecini Görüntüleme:

  ```sh
  tasklist | find "notepad"
  ```

`taskkill` komutu belirli bir süreci sonlandırmak için kullanılır. Zorlama kapatmak için idealdir.

- Belirli Bir Süreci PID ile sonlandırmak :

  ```sh
  taskkill /PID 1234
  ```

- Süreç Adıyla Sonlandırma :

  ```sh
  taskkill /IM notepad.exe
  ```

- Süreci zorla Sonlandırma :

  ```sh
  taskkill /F /PID 1234
  ```

  ```sh
  taskkill /IM uygulama.exe /F
  ```

  **/F** parametresi, süreci zorla kapatır. Eğer bir uygulama yanıt vermiyorsa bu seçenek kullanışlıdır.

#### 11. `ipconfig` Komutu

`ipconfig` komutu ip yapılandırması hakkında bilgi verir.

- Tüm IP yapılandırmasını listeleme :

  ```sh
  ipconfig
  ```

  Komutun çıktısı buna benzer görünecektir.

  ```plaintext
  Windows IP Configuration

    Ethernet adapter Ethernet:

        Connection-specific DNS Suffix  . : example.com
        IPv4 Address. . . . . . . . . . . . : 192.168.1.10
        Subnet Mask . . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . . . : 192.168.1.1

    Wireless LAN adapter Wi-Fi:

        Connection-specific DNS Suffix  . :
        IPv4 Address. . . . . . . . . . . . : 192.168.1.15
        Subnet Mask . . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . . . : 192.168.1.1
  ```

- IP yapılandırmasının detayları :

  ```sh
  ipconfig /all
  ```

  Komutunun çıktısı :

  ```plaintext
  Windows IP Configuration

   Host Name . . . . . . . . . . . : MYCOMPUTER
   Primary Dns Suffix . . . . . . . : example.com
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No


  Ethernet adapter Ethernet:

  Connection-specific DNS Suffix . : example.com
  Description . . . . . . . . . . . . : Intel(R) Ethernet Connection
  Physical Address. . . . . . . . . . : 00-1A-2B-3C-4D-5E
  DHCP Enabled. . . . . . . . . . . . : Yes
  Autoconfiguration Enabled . . . . . : Yes
  IPv4 Address. . . . . . . . . . . . : 192.168.1.10
  Subnet Mask . . . . . . . . . . . . : 255.255.255.0
  Default Gateway . . . . . . . . . . . : 192.168.1.1
  DHCP Server . . . . . . . . . . . . : 192.168.1.1
  DNS Servers . . . . . . . . . . . . : 8.8.8.8
  8.8.4.4
  Lease Obtained. . . . . . . . . . . . : October 27, 2024 09:30:00 AM
  Lease Expires . . . . . . . . . . . . : October 28, 2024 09:30:00 AM

  Wireless LAN adapter Wi-Fi:

  Connection-specific DNS Suffix . :
  Description . . . . . . . . . . . . : Intel(R) Wireless-AC 8265
  Physical Address. . . . . . . . . . : 00-1A-2B-3C-4D-5F
  DHCP Enabled. . . . . . . . . . . . : Yes
  Autoconfiguration Enabled . . . . . : Yes
  IPv4 Address. . . . . . . . . . . . : 192.168.1.15
  Subnet Mask . . . . . . . . . . . . : 255.255.255.0
  Default Gateway . . . . . . . . . . . : 192.168.1.1
  DHCP Server . . . . . . . . . . . . : 192.168.1.1
  DNS Servers . . . . . . . . . . . . : 8.8.8.8
  8.8.4.4
  Lease Obtained. . . . . . . . . . . . : October 27, 2024 09:30:00 AM
  Lease Expires . . . . . . . . . . . . : October 28, 2024 09:30:00 AM
  ```

- `ipconfig /release` ve `ipconfig /renew` Komutu

  `ipconfig /release` komutu bilgisayarımızın DHCP suncusundan aldığı `IP` adresini bırakır.
  `ipconfig /renew` komutu DHCP sunusundan yeni `IP` adersi alınmasını sağlar.

  ```sh
  ipconfig /release
  ipconfig /renew
  ```

  Komutu ile DHCP suncusundan mevcut `IP` bırakılarak yeni bir `IP` alınır.

#### 12. `ping` Komutu

Bir ağ cihazına ulaşılabilirliği test etmek için kullanılır. Domain veya ip ile test edilebilir.

```sh
  ping www.google.com
```

çıktı

```plaintext
  Pinging www.google.com [142.250.185.78] with 32 bytes of data:
  Reply from 142.250.185.78: bytes=32 time=14ms TTL=117
  Reply from 142.250.185.78: bytes=32 time=13ms TTL=117
  Reply from 142.250.185.78: bytes=32 time=12ms TTL=117
  Reply from 142.250.185.78: bytes=32 time=11ms TTL=117

  Ping statistics for 142.250.185.78:
      Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
  Approximate round trip times in milli-seconds:
      Minimum = 11ms, Maximum = 14ms, Average = 12ms
```

veya

```sh
  ping 192.168.1.19
```

çıktı

```plaintext
  Pinging 192.168.1.19 with 32 bytes of data:
  Request timed out.
  Request timed out.
  Request timed out.
  Request timed out.

  Ping statistics for 192.168.1.19:
      Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),
```

#### 13. `netstat` Komutu

Genellikle aktif ağ bağlantıları ve hangi portların dinlendiğini görmek için kullanılır.

```sh
  netstat -an
```

Aktif bağlantıları ve hangi portların kullanıldığını görmek için bu komutu yazarız. Çıktısıda şuna benzer birşey olacaktır.

```plaintext
  Proto  Local Address          Foreign Address        State
  TCP    0.0.0.0:80            0.0.0.0:0              LISTENING
  TCP    192.168.1.5:49152     203.0.113.5:80        ESTABLISHED
  UDP    0.0.0.0:123           *:*
```

Sadece belirli bir portu sorgulamak için şöyle bir komut yazabiliriz.

```sh
  netstat -an | findstr :80
```

çıktısı

```plaintext
  TCP    0.0.0.0:80            0.0.0.0:0              LISTENING
  TCP    192.168.1.5:49152     203.0.113.5:80        ESTABLISHED
```

Burada, 80 numaralı portun durumu ve hangi IP adreslerine ait olduklarını görebiliriz.

#### 14. `systeminfo` Komutu

`systeminfo` komutu windows ve cihaz donanımı hakkında bazı detay bilgileri verir.

```sh
  systeminfo
```

çıktısı

```plaintext
  Host Name:                MYCOMPUTER
  OS Name:                  Microsoft Windows 10 Pro
  OS Version:               10.0.19042 N/A Build 19042
  OS Manufacturer:          Microsoft Corporation
  System Manufacturer:      Dell Inc.
  System Model:             XPS 15 9570
  Processor(s):             Intel(R) Core(TM) i7-8750H CPU @ 2.20GHz
  Total Physical Memory:    16,384 MB
  Network Card(s):          1 NIC(s) Installed.
```

#### 15. `sfc /scannow` Komutu

Windowsun sistem dosyalarını tarar ve bozuk dosyaları onarır. İnternet bağlantısına ihtiyaç duymaz. Bozuk olan dosyaları windowsun kendi yedeklerinden geri döndürür.

```sh
  sfc /scannow
```

```plaintext
  Windows Resource Protection did not find any integrity violations.
```

Komutun çıktı mesajında durumdan sizi haberdar edecektir.

#### 16. `chkdsk` Komutu

`chkdsk` komutu windows işletim sistemindeki disklerin hatalarını bularak onarmak için kullanılan bir komuttur.

```sh
  chkdsk C: /f /r
```

Bu komutun parametlerinden bahsedecek olursak,

- **C:** : Hangi diskin kontrol edileceğini bildirir.
- **/f** : Bulunan hataları düzeltmek için komutun çalışmasını sağlar.
- **/r** : Kötü sektörleri bulur ve onarmaya çalışır, ayrıca bu kötü sektörlerdeki okunabilir bilgileri kurtarmaya çalışır.

Eğer sadece diskinizi kontrol etmek istiyorsanız.

```sh
  chkdsk C:
```

#### 17. `shutdown` Komutu

Bilgisayarı kapatmak , yeniden başlatmak ve oturumu kapatmak için kullanılır.

- Bilgisayarı kapatmak için

  ```sh
  shutdown /s /t 0
  ```

- Bilgisayarı yeniden başlatmak için

  ```sh
    shutdown /r /t 0
  ```

- Cihazın 60 saniye sonra kapanması için
  ```sh
    shutdown /s /t 60
  ```

#### 18. `get-help` Komutu

`get-help` komutu arkasına yazılan komut hakkında syntax, kullanım amacı ve şekli hakkında bilgiler verir.

```sh
  get-help get-process
```

komutun çıktısı şöyle olacaktır.

```plaintext
    NAME
    Get-Process

    SYNOPSIS
        Gets the processes that are running on your local computer or a remote computer.

    SYNTAX
        Get-Process [[-Name] <String[]>] [-Module] [-FileVersionInfo] [-InputObject <Process[]>] [-PassThru]
        ...

    DESCRIPTION
        The Get-Process cmdlet gets the processes that are running on your local computer or a remote computer.
        You can use the Name parameter to get specific processes by name.

    PARAMETERS
        -Name <String[]>
            Specifies the process names of the processes to get.

        -Module
            Gets the processes that are running on the computer.

    EXAMPLES
        -------------------------- EXAMPLE 1 --------------------------
        Get-Process
            Gets all the processes that are running on the local computer.

        -------------------------- EXAMPLE 2 --------------------------
        Get-Process -Name notepad
            Gets the Notepad processes that are running on the local computer.
```

Umarım rehber yardımcı olacaktır. Yazı veya başka bir konuda blogtaki kanallardan iletişime geçebilirsiniz. MAA
