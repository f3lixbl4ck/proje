Yazılım – MMJoy
Projenin yazılım kısmı en az elektronik kısmı kadar basit. Hazırladığımız donanımı oyun koluna dönüştürmek için MMJoy isminde yine bu hobi ile uğraşanların yazmış olduğu bir programı kullanacağız. Yani bu projeyi yapmak için bir kodlama bilgisine veya teknik bilgiye ihtiyacınız yok.

İşe MMJoy’u indirerek başlayalım. Aşağıdaki link üzerinden projeyi indirelim ve dosyaları sıkıştırılmış formattan çıkaralım.

https://github.com/MMjoy/mmjoy_en

Kullanacağımız program yüklediğimiz dosyanın içerisindeki “firmware and software release” klasöründeki .zip dosyasında yer alıyor.
“MMJoy2” klasörü projemizle alakalı tüm işi yürüteceğimiz ortam olacak. Bu klasörün içerisinde donanıma yükleyeceğimiz firmware dosyasından projeyi yaparken işimize yarayacak görsellere kadar çok sayıda içerik bulunuyor. Tüm ayarları ve kod yükleme işini ise yine bu klasörün içindeki “MMJoySetup” arayüzü üzerinden yapacağız.

Firmware Yüklemesi
Bu arayüz üzerinde yapacağımız ilk iş Arduino Leonardo kartını oyun koluna dönüştürecek olan yazılımı karta yüklemek olacak. Açılan arayüzdeki “Firmware” sekmesine geliyoruz. Burada çok sayıda buton ve textbox bulunuyor. Aşağıdaki görselde kırmızı ile işaretlenmiş alanda yükleme öncesi ayarları yapacağız.

“Firmware file” kısmında karta yükleyeceğimiz yazılımı seçeceğiz. Bu yazılım “MMJoy2” klasörü içindeki “Firmware” klasöründe yer alıyor. Klasöre giriş yaptığınızda .hex uzantılı 3 farklı dosya ile karşılacaksınız. Buradaki dosya seçimini kullandığımız donanıma göre yapmamız gerekiyor. Arduino Leonardo kartının üzerindeki mikrodenetleyici Atmega32u4 olduğundan önceki başlıkta bahsetmiştim. Bu yüzden “ATMEGA32U4” için hazırlanmış firmware dosyasını seçiyoruz.

Firmware dosyasını ekledikten sonra “Chip” kısmında “atmega32u4”; “Bootloader type” kısmında ise “Arduino”yu seçiyorum. “Port” seçiminde ise yanındaki “COM ports list” butonuna tıkladığınızda farklı portlar görebilirsiniz. Ancak port seçimini hemen yapmıyoruz.
Firmware yüklemesi yapmak için Arduino Leonardo’yu “bootloader” modunda yani “önyükleyici” modunda çalıştıracağız. Kart yaklaşık 8 saniye boyunca bootloader modundayken yüklemeyi tamamlamamız gerekiyor. Arduino normal konumunda ve bootloader konumunda farklı portlara bağlı olarak çalışır. Dolayısıyla yükleme işleminden önce kartın bootloader modundayken hangi porta bağlı olduğunu tespit etmemiz gerekiyor. “Port(arduino)” kısmını da buna göre dolduracağız.

Yine arayüz üzerindeki “Device management” butonuna tıklayarak “Aygıt Yönetici”sini açıyoruz. Açılan pencerede “Bağlantı Noktaları”na tıklayarak Arduino’nun bağlı olduğu portu görebilirsiniz.
Aygıt yöneticisini açtıktan sonra Arduino Leonardo üzerindeki butona ard arda iki kere basarak kartı bootloader moduna alıyoruz. Bu işlemden sonra aygıt yöneticisi de kendini güncelleyecektir. Tekrardan “Bağlantı noktaları”na tıklayarak Arduino Leonardo’nun bootloader modundayken bağlı olduğu portu görebilirsiniz.

Bootloader durumundaki portu bildiğimize göre tekrar arayüze gelerek “Port” kutusuna port ismini girebiliriz. Benim bilgisayarımda “COM6” olduğu için bu şekilde devam ediyorum. Port kısmını da doldurduktan sonra kartı tekrar bootloader moduna alarak firmware yüklemesini yapmamız gerekiyor. Kart üzerindeki butona tekrar çift tıklıyoruz ve “Upload firmware” butonuna tıklıyoruz. Kartın bootloader modunda kalma süresinin yaklaşık 8 saniye olduğunu hatırlatmak isterim.

Şimdi karta bağlı olan potansiyometrenin ayarlarını yapalım.

Diğer Ayarlar
MMJoy çok sayıda donanımla çalışmanıza ve ayar yapmanıza olanak sağlayan bir program. Ancak bu projede tek bir potansiyometre bulunduğu için yalnızca bu potansiyometrenin ayarını yapacağız.

Firmware güncellemesinden sonra arayüzün sol üst kısmındaki cihaz listesinde bir farklılık göreceksiniz. Bilgisayarınız bundan sonra Arduino Leonardo’yu joystick olarak algılayacaktır. “Device list” kısmından kendi donanımımızı seçiyoruz. Sağ taraftaki bölümden donanımınızın ismini değiştirebilirsiniz.
Listede kendi donanımızı seçtikten sonra arayüzdeki “Joysticks axes” sekmesine geliyoruz. Aşağıdaki görselde işaretlenmiş alanlarda bazı ayarlar girmemiz gerekiyor.
Potansiyometreyi A0 pinine bağlamıştık. Kart üzerindeki A0 pini mikrodenetleyici üzerindeki “PF7” pinine bağlı olduğundan “MCU Port” kısmında “F7″yi seçiyorum. Karttaki pin numaralarının mikrodenetleyici üzerindeki karşılığını aşağıdaki görselde görebilirsiniz. 

http://ilgeipek.com/wp-content/uploads/2020/11/Pins_Arduinoleonardo-1024x596.jpg

“Source” kısmını “IntSensor” ve ekseni “X” olarak seçiyorum. “Precision” ayarında “10” sayısını seçmemizin sebebi Arduino Leonardo’nun 10bitlik bir analog-dijital çeviriciye sahip olması. Burası biraz daha teknik bir detay gibi gelebilir, ancak ayar yaparken burayı “10” yapmanız yeterli. Tğm ayarları yukarıdaki görselde paylaştığım gibi tamamlıyorum ve “Save sets to device” diyerek ayarları karta yüklüyorum.
Yükleme işleminden sonra donanımımız direksiyon olarak kullanılmaya hazır. Tüm parçaları montajlayalım ve test edelim!
