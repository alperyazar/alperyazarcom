Türkçe Ubuntu Üzerinde MATLAB Çalıştırma Problemi ve Çözümü
===========================================================

Geçen günlerde Ubuntu 10.04 nam-ı diğer "Lucid Lynx" üzerine MATLAB R2010b kurdum.

Kurulum esnasında programı, "PATH"'e eklemediğim için konsol üzerinden direkt olarak

.. code-block:: bash

  matlab

yazarak çalıştıramıyorum. Gerçi bunun çözümü kolay, problem bu değil. Fakat kurulum esnasında soruyor olması lazım. Rahatlık sağlaması açısından unutmamanızı öneririm. :)

"MATLAB Ubuntu'da nasılmış?" diye kurcalarken bir grafik çizdirip, lejant koymayı denedim. Fakat lejant koymaya çalışınca 2-3 adet hata oluşuyor ve lejant çıkmıyordu. Örneğin, en basitinden şu kodlar düzgün çalışmıyordu:

.. code-block:: matlab

  x=0:0.1:5;

  y=2+x;

  plot(x,y)

  legend('y=2+x')

Yukarıdaki kodu çalıştırdıktan sonra şu cümleyle başlayan hatalar aldım:

.. code-block:: none

  **No appropriate method, property, or field itemTokenSize for class scribe.legend.**

Grafik çizilse bile, yakınlaşma gibi düğmeler çalışmamaktaydı. Biraz araştırma yaptıktan sonra http://www.mathworks.com/matlabcentral/newsreader/view_thread/288923 adresli sayfayı buldum. Kişilerden biri, bunun MATLAB 2010a'nın Türkçe LINUX işletim sistemi üzerinde çalışması sonucu olan bir **bug** olduğunu düşünüyor. Önerdiği çözüm ise oldukça basit:

Eğer MATLAB'ı

.. code-block:: bash

  matlab

komutu ile çalıştırıyorsanız

.. code-block:: bash

  LC_ALL=C matlab

komutu ile çalıştırarak. Veya benim gibi unutkansanız ve MATLAB'ı şuna benzer bir şekilde çalıştırıyorsanız:

.. code-block:: bash

  /usr/local/MATLAB/R2010b/bin/matlab

yerine

.. code-block:: bash

  LC_ALL=C /usr/local/MATLAB/R2010b/bin/matlab

komutu ile çalıştırarak bu sorunu çözebilirsiniz. Komutları bu şekide değiştirdiğiniz zaman yukarıda verdiğim MATLAB kodu sorunsuzca çalışmaktadır.

Bu sorun hakkında tam bir kaynak bulamsam da yukarıda da bahsettiğim gibi iddalar dili Türkçe olan LINUX işletim sisteminden kaynaklandığı doğrultusunda. Zaten eklediğimiz kod ile dil ile ilgili değişiklik yapıyoruz. Bknz: http://www.linuxquestions.org/questions/fedora-35/c-locale-and-system-locale-304562/

Güncellendi: -

Oluşturuldu: 20 Mart 2011
