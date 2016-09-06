3. Gerçek Robot'un Kontrolüne Erişin
====================================

Gerçek bir MRP2'yi başlatın ve onu kontrol edin!

1. Robot'u açma
---------------

Robotu açmak için tek yapmanız gereken şey robotun kullanıcı panelindeki güç düğmesine basmak. Basınca bir süre, sistem açılana kadar düğmenin led'i yanıp sönecektir. Led in yanıp sönmesi bitip tamamen yanmaya başladığında robotunuz açılmış ve kullanıma hazırdır.

2. Robot'a Erişin
-----------------

MRP2'nin ROS ağına kişisel bilgisayarınızdan erişmek için Ubuntu PC'nizden, robot ile kişisel bilgisayarınızın aynı ağda olduğuna emin olduktan sonra, aşağıdaki iki komutu girmelisiniz. Ayrıca bu komutları açtığınız her terminal ekranında girmelisiniz:

.. warning::

    Don't forget to replace ``<IP_OF_...>`` sections with real ip's.

::

    $ export ROS_MASTER_IP=http://<IP_OF_MRP2_ONBOARD_COMPUTER>:11311


::

    $ export ROS_HOSTNAME=<IP_OF_YOUR_PC>

Her seferinde uğraşmak istemiyorsanız ``.bashrc`` dosyanıza ekleyebilirsiniz: 

::

    $ echo "export ROS_MASTER_IP=http://<IP_OF_MRP2_ONBOARD_COMPUTER>:11311" >> ~/.bashrc

::

    $ echo "export ROS_HOSTNAME=<IP_OF_YOUR_PC>" >> ~/.bashrc

Bu iki komut ``.bashrc`` dosyanızın sonuna eklendikten sonra bir defaya mahsus o anki terminalinizde aşağıdaki komutu girin:

::

    $ source ~/.bashrc 

Artık, bu terminal penceresinden bir ROS programı başlatırsanız, robotun bilgisayarında çalışan ``ros_master`` node'u ile haberleşecektir. Örnek olarak ``rqt_robot_steering``'i çalıştırarark robotu sürebilirisiniz. Ya da robot tarafında ``gmapping`` ya da ``amcl`` çalışıyorsa Rviz çalıştırıp izleyebilirisiniz. RViz robotun bilgisayarındaki topic'lerden okuyacaktır. Robot tarafında nasıl gmapping'i çalıştıracağınızı bilmiyorsanız, bir sonraki kılavuzda anlatılacaktır.

.. note::
	
	Bu satırları ``.bashrc`` dosyanıza eklediğinizde, her seferinde ``source`` etmenize gerek kalmaz. Bu dosya, bir terminal açıldığında otomatik olarak okunmaktadır. Ek olarak, eğer bu satırlar ``.bashrc`` dosyanıza eklenmişse, Gazebo Simülasyonu gibi yerel uygulamaları açamazsınız. Yerel ağda bir uygulama başlatmak için açmış olduğunuz terminale sürekli aşağıdaki komutları girmeniz gerekir, Bu komutlar ``ROS_HOSTNAME`` ve ``ROS_MASTER_IP`` değişkenlerini bir önceki kılavuzlarda belirttiğimiz gibi sıfırlar:

	::

		$ export ROS_MASTER_IP= $$ export ROS_HOSTNAME=
    
Robot açıldıktan sonra joystick veya bir başka yöntemle sürebilirsiniz. Eğer kişisel bilgisayarınızdan kontrol etmek istiyorsanız, ``rqt_robot_steering``'i ip ayarları yapılmış terminalinizden çalıştırabilirisiniz:

::
		
	$ rosrun rqt_robot_steering rqt_robot_steering 

Eğer ``ros_master`` ile ilgili hata alırsanız, ``ROS_HOSTNAME`` ve ``ROS_MASTER_IP`` yi kontrol ediniz.