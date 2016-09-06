Bazı kullanışlı ROS Node'ları
=============================

Daha fazlası için `ROS Wiki <http://wiki.ros.org>`_ sitesini gezmenizi öneririz.

`roslaunch <http://wiki.ros.org/roslaunch>`_
--------------------------------------------

``roslaunch`` parametre sunucusunda parametre ayarı yapabildiği gibi, çoklu nodları yerelde ve uzakta SSH ile kolayca çalıştıran bir araçtır. Ölmüş bulunan işlemleri respawn edebilme gibi özellikler barındırır. Çalıştırılması gereken işlemleri çalıştırabildiği gibi, node'lara parametre ayarı yapan bir veya birden fazla XML ayar dosyasını(``.launch`` uzantısına sahip) da içerebilir, kapsayabilir.

``roslaunch`` takes in one or more XML configuration files (with the ``.launch`` extension) that specify the parameters to set and nodes to launch, as well as the machines that they should be run on.

Çoğu ROS paketi, aşağıdaki şekliyle çalıştırabileceğiniz gibi ``.launch`` dosyalarıyla gelir:

::
	
	$ roslaunch package_name file.launch


`rqt_console <http://wiki.ros.org/rqt_console>`_ and `rqt_logger_level <http://wiki.ros.org/rqt_logger_level>`_
---------------------------------------------------------------------------------------------------------------------------------------------------

``rqt_console`` ROS Mesajlarını filtreleyip gösterebilmek için arayüz eklentisi sunar. Ve ``rqt_logger_level`` ise ROS mesajlarının filtreleme ayarlarının yapılabilmesi için yapılmış arayüz eklentisidir. Ayrıca ``rqt_logger_level``'ı başka bir terminalden açmak zorunlu değildir. ``rqt_console`` ekranında zaten açmak için bir buton bulunur. Aşağıdaki paketlerin kurulu olduğuna emin olduktan sonra;

::
	
	$ sudo apt-get install ros-indigo-rqt ros-indigo-rqt-common-plugins 

Bu node'ları şu komutlarla açabilirisiniz:

::
	
	$ rosrun rqt_console rqt_console

::
	
	$ rosrun rqt_logger_level rqt_logger_level

Daha önceki kılavuzlardan **Basit bir Haberleşme Örneği** kısmında ``ROS_INFO(...)`` fonksiyonunu kullandık. ROS Node'umuz, bu fonksiyon çalıştığında eğer logger level'ımız ugunsa, mesajı konsol ekranına yazar ve ``rqt_console``'da da görürüz. bir diğer örnek, Eğer logger level'ımız ``Debug`` değilse, ``ROS_DEBUG(...)`` fonksiyonlarının mesajlarını asla görmeyiz.

`roswtf <http://wiki.ros.org/roswtf>`_
--------------------------------------

Bu komut, tüm sisteminizi yoklayarak sorunları araştırır ve bulur. Node'larınızı çalıştırdığınızda anlamadığınız bir hata alırsanız bir de bu komutun çıktısına bakınız:

::
	
	$ roswtf

`rosbag <http://wiki.ros.org/rosbag>`_
--------------------------------------

``rosbag``, ROS topic'lerinden veri okuyan ve sonra geri basabilen araçlar barındırır. Deserialization ve reserialization kısımlarını atladığı için yüksek performansla çalışır.


Bu komutu denemek için bir önceki örneklerden; **Basit bir Haberleşme Örneği**, **Navigation** ya da basitçe, MRP2'yi gazebo'da çalıştırıp bir süreliğine sürebilirsiniz. Sürmeden önce aşağıdaki komutları girin:

::
	
	$ mkdir ~/bagfiles

::
	
	$ cd ~/bagfiles

::
	
	$ rosbag record -a

Ve robotu joystick veya ``rqt_robot_steering`` plugin'i ile sürün. Ve ``rosbag``'i açmış olduğunuz terminale dönüp ``Ctrl + C`` ile çalışan işlemi kapatın. Diğer ROS Node'larını da kapattıktan sonra ``mrp2_gazebo.launch``'ı tekrar açın. Ve ``bagfiles`` klasöründeyken topic'lere aynı verileri geri basmak için aşağıdaki komutu çalıştırın:

::
	
	$ rosbag play <YOUR_BAG_FILE_NAME.bag>

Çalıştırır çalıştırmaz, Gazebo ekranına dönün ve robotunuzun geçmişindeki gibi hareket ettiğini göreceksiniz...
