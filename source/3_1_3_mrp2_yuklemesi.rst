3. ROS'u öğrenmek için MRP2 Paketlerini Yükleme
===============================================

MRP2, diğer ROS yüklü robotların birçoğu gibi açık kaynak kodludur. Github'da genele açık repository'leri bulunmaktadır. Bunları yüklemek için önce workspace'inizin ``src`` klasörüne girin:

::
	
	$ cd ~/catkin_ws/src

Ve aşağıdaki komutları sırasıyla çalıştırın:

::
	
	$ git clone https://github.com/milvusrobotics/mrp2_common.git
	$ git clone https://github.com/milvusrobotics/mrp2_desktop.git
	$ git clone https://github.com/milvusrobotics/mrp2_simulator.git

Sonra bir üst klasöre aşağıdaki komutla çıkın (bu örnekte, ``~/catkin_ws/`` dizini oluyor):

::
	
	$ cd ..

Şimdi ``rosdep`` ile tüm paket gereksinimlerini yüklemeniz gerekiyor:

::
	
	$ rosdep install --from-paths src --ignore-src --rosdistro=indigo -y

Bu komut, ``src`` klasörünüzdeki paketlerin gereksinimlerini otomatik olarak bulur ve yükler. Şimdi, ``catkin_make`` komutunu kullanarak workspace'inizi build edebilirisiniz:

::
	
	$ catkin_make

Yine de, bu paketler, Milvus Robotics tarafından devamlı olarak geliştirilmektedir. Eğer ``catkin_make`` bir paket ile ilgili hata verirse, paketin ismini aşağıdaki kalıba uydurarak yüklemeyi deneyebilirisiniz:

::
	
	$ sudo apt-get install ros-indigo-<NAME OF THE PACKAGE WHICH GIVES AN ERROR>

Paket adlarını bulmak için internette arama da yapabilirsiniz.

.. note::
	
	Paketin adını denemeye başlayın, ve tab tuşuna basın. Eğer paket adını tam bulmuşsanız tab tuşuna basmanız konutu tamamlayacaktır. Eğer girdiğiniz isimle başlayan birden fazla paket varsa, Tab tuşuna iki defa basmanız olası paket isimlerini listeler. Bir defa tab tuşuna basmayı aşağıdaki komutla deneyebilirsiniz:

	::
		
		sudo apt-get install lov

	İki kere basmayı da şununla:

	::
		
		sudo apt-get install morse

	Sonra dilerseniz bu paketleri yükleyin, ya da enter'lamadan terminali kapatın.








