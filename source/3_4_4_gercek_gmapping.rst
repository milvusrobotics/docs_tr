4. Robotunuzla Gerçek bir Harita Çıkarın
========================================

Gerçek bir alanı robotun gözünden keşfedin ve haritasını kaydedin.
	
1. Robotu Açın
--------------

If the robot is already running, you can pass to second section directly. Otherwise you can turn back to previous tutorial and access control of it.

2. Gmapping Uygulamasını Açın
-----------------------------

Şimdi, Eş Zamanlı Konumlama ve Haritalama uygulamasını (*Simultaneous Localization and Mapping*, SLAM) açabiliriz. Kendi PC'nizde bir terminal açın ve ilk önce SSH ile robota bağlanın, ``<IP_OF_ROBOT>`` kısmını robotun ip'si ile değiştirip aşağıdaki komutu girin :

::
	
	$ ssh mrp2@<IP_OF_ROBOT>

Robot bilgisayarındaki ``mrp2`` kullanıcısının varsayılan şifresi ``temppwd``'dir.

Bağlandıktan sonra o terminale aşağıdaki komutu girin:

::
	
	$ roslaunch mrp2_navigation gmapping_demo.launch

Şimdi, Gmapping uygulaması başladı ve robot harita çıkararak kendisini harita üzerinde konumlandırmaya başladı. Artık, bir önceki kılavuzlarda gösterildiği gibi joystick ile veya istediğiniz bir başka yöntemle robotu kontrol edebilirsiniz. Eğer ``rqt_robot_steering`` ile kontrol etmek isterseniz, yeni bir terminal penceresi açın ve ``rqt_robot_steering``'i çalıştırın:

::
	
	$ rosrun rqt_robot_steering rqt_robot_steering


3. Gmapping işlemini RViz ile Görselleştirin
--------------------------------------------

Gmapping çalışıyor ama robotun içnde nelerin döndüğünü bizim de görmemiz gerek. PC'nizde diğer bir terminali açın ve şunu yazın;

::
	
	$ roslaunch mrp2_viz view_gmapping.launch


Sonunda simülasyondaki dünyayı robotun bildiği kadarıyla bir kısmını 2B olarak görebiliyoruz. RViz'de robotu interactive marker'lar ile kontrol edebilir, robota, gitmesi için basit hedefler yollayabilirisiniz. 

.. figure:: _static/gmapping_real.png
   :align: center

Eğer keşfiniz tamamlandıysa, istediğiniz zaman haritayı kaydedebilirsiniz, bir diğer terminal açın ve SSH ile robota bağlanın, ``<IP_OF_ROBOT>`` kısmını robotun ip'si ile değiştirip aşağıdaki komutu girin: 

::
	
	$ ssh mrp2@<IP_OF_ROBOT>


ve haritayı kaydedin; eğer adının ``my_new_map`` olmasını isterseniz, aşağıdaki komutu çalıştırın;

::
	
	$ rosrun map_server map_saver -f /home/mrp2/my_new_map

Bu komut, ``new_map.pgm`` ve ``new_map.yaml`` adında iki dosya oluşturur. Bu dosyaları daha sonra ``amcl`` uygulamasıyla kullanabiliriz. Nasıl olduğunu öğrenmek için bir sonraki kılavuza bakabilirisiniz. Simülasyondaki ``amcl`` ile aynı şekilde çalışır. Zaten büyük ihtimalle anlamış olduğunuz üzere bu kullanımda ``map_server`` robot tarafında çalışıyor ve haritayı robotun bilgisayarına kaydediyor.
