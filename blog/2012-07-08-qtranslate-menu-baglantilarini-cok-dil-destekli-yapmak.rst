qTranslate: Menu Bağlantılarını Çok Dil Destekli Yapmak
=======================================================

Bir önceki yazımda, qTranslate adlı WordPress eklentisi ile WordPress sitenizi nasıl çok dil destekli hale getirebileceğinizden bahsetmiştim. Eklenti menüler dahil olmak üzere birçok metni çok dil destekli yapabiliyor. Buradaki menüden kastım, WordPress yönetim paneliniz üzerinden Görünüm -> Menüler araclığı ile düzenlediğiniz menüler oluyor. Tabi kullandığnız temanın da menü desteği sunması gerekiyor. Eğer menüleri el ile tema dosyasını değiştirirek koyduysanız yani menüleri statik olarak oluşturduysanız bahsettiğim yöntem sizin için geçerli olmayacaktır

Normalde, qTranslate birçok alanı işleyip, dile uygun menüler oluşturabiliyor. Örneğin menü isimlerini böyle ayarlayabilmeniz mükün. Fakat menüde oluşturduğunuz bir bağlantı WordPress sayfasına değil de, dış bir URL'ye açılıyorsa dile uygun bağlantı oluşturmak çok kolay olmayabiliyor veya ben beceremedim. :) Bağlantının URL kısımına qTranslate'in anlayacağı şekilde bir kod yazmanız pek mümkün olmuyor. Mesela:

.. code-block:: none

  [:Dil1]http://www.dil1baglantisi.com[:Dil2]http://www.dil2baglantisi.com

şeklinde bir URL yazıp, kaydet dediğiniz zaman URL kısmı boş dönüyor. Muhtemelen veritabanına kaydedilmeden önce WordPress'te bulunan bir filtre, URL'nin, doğal olarak, geçersiz olduğunu düşünüp, kaydı değiştiriyor. Bu noktada bir şekilde URL filtresini devre dışı bırakmak çözüm olabilir. Fakat ben veritabanına direkt müdahele ederek URL'yi elle eklemeyi tercih ettim.

Öncelikle veritabanına phpMyAdmin gibi bir arayüzle ulaşıyoruz. Menü bağlantıları "postmeta" tablosunda tutluyor. Eğer WordPress kurulumunda tablo ön ekini değiştirmediyseniz veritabanınzda "wp_postmeta" adlı bir tablo olması gerekiyor. Bunu açıyoruz. Bağlantı satırlarının "meta_key" sütünün değeri "_menu_item_url" oluyor. Bu sayede biraz karışıtırarak değiştirmek istediğimiz URL'yi buluyoruz. Ve yukarıda verdiğim formatta URL'yi kaydediyoruz. qTranslate kullnıyorsanız yukarıdaki formata çok yabanacı olduğunuzu zannetmiyorum. Dil1, Dil2 yazan yerlere kullandığımız dillerin kodlarını yazıyoruz. Türkçe için tr, İngilizce için en gibi. Sayfanız Dil1 dilinde gözükürken bağlantıya tıklandığı zaman www.dil1baglantisi.com'a, Dil2 dilinde gözükürken de www.dil2baglantisi.com'a yönleniyor. Veritabanındaki URL'yi yönetici panelinizde Görünüm -> Menüler aracılığı ile görebilmeniz mümkün. Fakat sakın düzenleyip, kaydete tıklamayın yoksa format olarak aslında geçersiz bir URL yazdığımızdan yine URL sıfırlanacaktır.

Güncellendi: -

Oluşturuldu: 8 Temmuz 2012
