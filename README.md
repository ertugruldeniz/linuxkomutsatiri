Selam arkadaşlar, bu yazımda sizlere tüm Linux dağıtımlarında sıkça kullanılan komutların ne anlama geldiğini ve nasıl kullanı	ldığını anlatmaya çalışacağım. Komut satırında bir işlemi gerçekleştirebilmek için belirli komutların bilinmesi gerekir.
Çoğu zaman komutlar üç ana bölümden oluşur.
<komut> <seçenek(ler)> <argüman(lar) 
	Seçenekler komutun nasıl çalışacağı belirler.
	Argümanlar ise komutun ne üzerinde çalışacağını belirler.
	Komutun çalışma durumuna göre seçenek ve ya argüman eklenmeyebilir.

Sistem bilgilerini öğrenmek için gereken bazı komutlar aşağıdaki gibidir.
uname  - >  Linux sistem bilgilerini gösterir. uname birçok parametre almaktadır.
 -a      Aşağıdaki tüm bilgileri tek seferde verir.
        -m      The machine (hardware) type
        -n      Hostname
        -r      Kernel release
        -s      Kernel name (default)
        -p      Processor type
        -v      Kernel version
        -i      The hardware platform
        -o      OS name

[root@localhost ~]# uname -a
Linux localhost 4.12.0-rc6-g48ec1f0-dirty #21 Fri Aug 4 21:02:28 CEST 2017 i586
GNU/Linux

uptime    -> Makinenin ne zamandan beridir çalıştığına dair yıl, ay, gün ve saat bazında bilgi vermektedir.
[root@localhost ~]# uptime
 22:31:07 up 13 min,  load average: 0.00, 0.00, 0.00

hostname -> Üzerinde çalışılan makinanı hostname adresini verir. hostname –i parametresi ile ip adresinide görebilirsiniz.
[root@localhost ~]# hostname
localhost
[root@localhost ~]# hostname -i
127.0.0.1

last reboot -> Sistemin önceden gerçekleştirdiği yeniden başlatma içeriğini gösterir.
[root@localhost ~]# last reboot
BusyBox v1.24.2 (2017-05-25 17:33:59 CEST) multi-call binary.
Usage: last
Show listing of the last users that logged into the system

date -> İşletim sisteminin sistem tarini ve saatini verir.
[root@localhost ~]# date
Sat Dec 29 22:37:49 UTC 2018

cal -> Takvimi cal komutu ile görüntülenebilir. İstenilen yıla ait takvim görüntülemek için cal komutu ve yılı yazmak yeterlidir.
whoami ->  whoami komutu online olan kullanıcıyı gösterir.
[root@localhost ~]# whoami
root

finger kullaniciadi -> Kullanıcı hakkında bilgi verir.
df   -> disk durumu hakkında bilgi  verir.
[root@localhost ~]# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/root              1048576    454612    593964  43% /
devtmpfs                 61068         0     61068   0% /dev
tmpfs                    61224         8     61216   0% /run

du -> Dizinin kullandığı disk miktarını gösterir.
[root@localhost dos]# du
160     ./asm-1.9
196 

free ->  Kullanılan ram miktarını gösterir.
[root@localhost dos]# free
             total       used       free     shared    buffers     cached
Mem:        122448       5576     116872          8          0        716
-/+ buffers/cache:       4860     117588
Swap:            0          0          0

Günlük dosya işlemlerinde en çok kullanılan kullanılan bazı komutlar aşağıdaki gibidir.
ls   –> Dizin içerisinde bulunan dosyaları ve belgeleri listeler. 
[root@localhost dos]# ls
asm-1.9     asm.com     debug.com   hpigot.com  hpigot.s

ls –al   –>  Gizli dosyalar dahil tüm dosyaları listelemek için kullanılır.



cd dir - belirtilen dizine girer.
[root@localhost ]# ls
bin      etc      lib      linuxrc  mnt      proc     run      sys      usr
dev      home     lib32    media    opt      root     sbin     tmp      var
[root@localhost ]# cd etc/


cd   –> cd komutuna herhangi bir parametre vermezseniz ev dizinine geçiş yapar. 
pwd  –> mevcut dizini gösterir.
[root@localhost etc]# pwd
/etc

mkdir yenidosya – > Yenidosya isminde dizin oluşturur. 
rm yenidosya –>  yenidosya adındaki dizini siler.
rm -r dizin –>  Belirtilen dizini siler 
rm -f file –> Belirtilen dosyayı silmeye zorlar.
rm -rf dizin –> Belirtilen dizini silmeye zorlar.
cp elma armut –>  Elma adında bulunan dosyayı armut adındaki dosyaya kopyalar.
cp -r dizin1 dizin2   –>Dizin1'i dizin2'ye kopyalar; Dizin2 yoksa oluşturur.
mv dosya1 dosya2 – > dosya1'in adını dosya2 yapar.
ln -s dosya bağ – > Belirtilen dosyaya sembolik bağ oluşturur. 
touch dosya – > Boş dosya oluşturur.
cat > dosya – >  Dosyaya girdi yönlendirir.
more dosya – > Dosyanın içeriğini sayfalayarak gösterir.
head dosya –>  Dosyanın ilk 10 satırını gösterir.
Head 100 dosya -> Dosyanın ilk 100 satırını gösterir. 100 yerine görmek istediğiniz satır kadar sayı girebilirsiniz.
tail dosya – > Dosyanın son 10 satırını gösterir.
tail 20 dosya -> Dosyanın son 20 satırını gösterir. 
tail -f dosya –> dosyanın son 10 satırını eşzamanlı olarak gösterir.




Süreç yönetiminde kullanılan komutlar ;
ps ->  Sistemimizde aktif olan süreçlerin listesini gösterir.
[root@localhost ]# ps
PID   USER     COMMAND
    1 root     {init} /bin/sh /sbin/init
    2 root     [kthreadd]
    3 root     [kworker/0:0]
    4 root     [kworker/0:0H]
    5 root     [kworker/u2:0]
    6 root     [mm_percpu_wq]

top -> Tüm süreç bilgilerini gösterir.
kill PID  -> Süreci sonladırmak için kill kullanılır. PID top veya ps ile çıkan listedeki işin id’sidir.
killall proc -> Belirtilen tüm süreçleri sonlandırır.
bg -> Durdurulmuş işlemi arka planda yapmaya devam eder.
Fg -> Arkaplanda devam eden işi ön plana getirir.
clear ->  Çalışılan komut satırını temizleme işlemi yapar.

Dosya izinleri ;
chmod RAKAM dosyaadı – Belirtilen dosyanın izinlerini rakamsal olarak değiştirmeye yarar. 
Her rakam kullanıcı, grup ve diğerlerini ifade eder ve 3 hanede kullanılır:  
4 – okuma (r)  
2 – yazma (w) 
1 – çalıştırma (x) 
chmod 777  dosyaadi –> Dosyanın okunması, yazılması ve çalıştırılmasına izin verir.

Klavye Kısayolları
Ctrl+C – Komutu durdurur, sona erdirir.
Ctrl+Z – Komutu durdurur, devam etmek için fg arkaplanda devam için bg kullanılır.
Ctrl+D – Konsol oturumundan çıkış yapar. 
Ctrl+W –Mevcut satırda bir kelime siler. 
Ctrl+U – Tüm satırı siler. 
Ctrl+R – Komut geçmişinde arama yapar. !! - Son verilen komutu tekrarlar.
Ağ İşlemleri İçin Komutlar
ping hedef – hedefe ping atar ve sonuçları gösterir. 
whois domain – belirtilen alan adının kayıt bilgilerini gösterir.
dig domain – Belirtilen alan adının DNS bilgilerini gösterir. 
dig -x host – PTR kaydını gösterir. 
wget file – Belirtilen adresteki dosyayı indirir. 
wget -c file – Durdurulmuş indirmeye devam eder.

Arama İşlemleri için komutlar
grep ifade dosya – Belirtilen dosyalarda ifadeyi arar .
grep -r ifade dir –  Belirtilen dosyalarda ifadeyi özyineli aratır. 
komut | grep ifade – Komutun çıktısında ifadeyi aratır
locate dosya – Belirtilen dosyayı aratır. 

Yardım Komutları
man <komut> Komutların kılavuz dosyalarını açar.
<komut> --help Komutun kullanımıyla ilgili bilgi verir.
Bash Değişkenler
 Export DEG=icerik     #DEG değerine içerik
 $PATH Çalıştırılabilir yollar 
$HOME Ev dizini 
$SHELL Çalışan kabuk 
env Ortam değişkenleri 
echo $DEG DEG değişken yazdır.


       Ertugrul Deniz    -   Temel Linux Komutları    -  ertugruldeniz.com  -  01.01.2019                                                                      
