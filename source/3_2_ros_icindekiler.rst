4. ROS'un İçindekiler
=====================

Giriş kısmının altındaki **Ana Mimariye Genel bir Bakış** kısmında bahsettiğimiz gibi; Node'lar, Topic'ler ve Parametreler ROS'un önemli birer parçalarıdır. 

Bu kılavuzu izleyebilmek için, ilk önce, gazebo'da MRP2'yi çalıştırın:

::
	
	$ roslaunch mrp2_gazebo mrp2_gazebo.launch

ve bu pencereyi küçültün. Bu ``.launch`` dosyası ``roscore``'un, bazı node'ların ve topic'lerinin açılmasını sağlamaktadır.


4.1 Node'lar
------------

Daha önce bahsedildiği gibi, bir node, çalıştırılabilir bir ROS paketinden başka birşey değildir.

Başka bir node'u elle çalıştırmak için, ``rosrun`` komutunu kullanabiliriz. Şimdi, bir joystick'iniz bulunmuyorsa veya bulunuyor ama robotun kontrolünde ikinci bir söz sahibi oluşturmak isterseniz, bir diğer terminal ekranını açın ve ``rqt_robot_steering``'i çalıştırın:

::
	
	$ rosrun rqt_robot_steering rqt_robot_steering

Eğer üst kısımdaki kutucuk içindeki topic adı doğruysa, şimdi robotunuza bu pencere vasıtasıyla hız komutları gönderebilirsiniz. Şimdi de başka bir terminal ekranı açıp şunu yazın:

::
	
	$ rosnode list

Bu komut, o an çalışmakta olan node'ları listeler. Listede robot steering node'unu bulabilirsiniz. Sadece ``rosnode`` komutunu yazarak, bu komutu nasıl kullanacağınız hakkında küçük bir yardım görüntüleyebilirsiniz:

::
	
	$ rosnode


4.2 Topic'ler
-------------

Topic'ler, node'lar arasındaki mesajların değiş tokuş edilebildiği isimlendirilmiş veri yollarıdır. Node'lar bölümünde dile getirildiği gibi, node'lara iletişimleri için topic'ler sağlamalısınız. O anki node'lar arasındaki iletişimin bir grafiğini görmek için aşağıdaki komutu çalıştırın ve bekleyin:

::
	
	$ rosrun rqt_graph rqt_graph

Çalışan tüm node'ları ve aralarındaki topicleri görebilirsiniz. Şimdi de transfer edilen verileri görebiliriz. Önce tüm topic'leri listelemek için aşağıdaki komutu kullanın:

::
	
	$ rostopic list

Aralarından birini seçebilirsiniz. Bizim seçimimiz, odometri topic'i. Bu topic gazebo tarafından paylaşılmaktadır, gerçek robotta ise, basit ya da karmaşık driver'larla sensörlerden okuyarak topic'lere yayın yapan node'lar bulunur. Odometri verisini görmek için aşağıdakini girin:

::
	
	$ rostopic echo /mobile_base_controller/odom

Tek başına ``rostopic`` yazıp enter'layarak basit bir yardım görüntüleyebilirisiniz:

::
	
	$ rostopic


4.3 Mesajlar
------------

Mesajlar, gelişigüzel eklşenmiş veri yapıları veya diziler barındırabilir(C'deki ``struct``'lar gibi).

Odometri topic'inin veri tipini görmek için aşağıdakini yazın:

::
	
	$ rostopic type /mobile_base_controller/odom

Çıkan yanıt ``nav_msgs/Odometry`` olacaktır. 

Bu mesaj tipi hakkında bilgi edinmek içinde ``rosmsg`` komutunu kullanabiliriz:

::
	
	$ rosmsg show nav_msgs/Odometry


4.4 Parametereler
-----------------

Parametre sunucusu, paylaşımlı, çoklu değişken içerebilen ve ağ API'leri ile erişilebilen bir sözlük gibidir. Node'lar bu sunucuyu çalışma esnasında değişkenlerini saklamak amacıyla kullanır. Yüksek performansla çalışmak için tasarlanmamıştır, daha çok binary olmayan konfigürasyon benzeri verileri saklamak için idealdir.

``rosparam`` YAML dizgili dosyalarla Parametre Sunucusu üzerindeki verileri okuyup veya değiştirebiliriz. Ayrıca YAML'in parametre sunucusuyla deneysel bir kullanımını desteklemektedir. Bu kütüphane, sadece iç kullanımlara yöneliktir. Ayrıca ``rosparam``, roslaunch dosylarıyla da çağrılabilir.

Tüm parametreleri listelemek için:

::
	
	$ rosparam list

komutunu kullanın. ``roscore`` işlemini kapatmadıysanız, parametre sunucusu eski parametreleri saklayacaktır. Ama bir node, çalışma esnasında parametreyi değiştiriyorsa, haliyle parametre değişebilir ve bir önceki değeri kaybolur.

Eğer gazebo'yu kapatmamışsanız devam edin, kapatmışsanız da yukarıda belirtildiği gibi yeniden açın.

Parametre değerlerini ``rosparam get`` ve  ``rosparam set`` komutlarıyla okuyup değiştirebilirsiniz. O anki tüm parametrelerin listesini görüntülemek için ağşağıdakini girin:

::
	
	$ rosparam list

Parametrelerden birinin değerini okumak için, bir tanesini seçin ve aşağıdaki komutta ``<PARAMETRE_ADI>`` kısmının yerine yazın:

::
	
	$ rosparam get PARAMETRE_ADI

Aşağıdaki ``set`` ile de değerini değiştirebilirsiniz:

::
	
	$ rosparam set PARAMETRE_ADI YENI_DEGER















