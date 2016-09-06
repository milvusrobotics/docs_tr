2. Workspace Oluşturma
======================

Kişisel uygulamaları oluşturmak için bir workspace'e ihtiyacımız var. Aşağıdaki komutlarla klasör oluşturup, içerisine girip, ``catkin_init_workspace`` komutunu çalıştırın:

::
	
	$ mkdir -p ~/catkin_ws/src
	$ cd ~/catkin_ws/src
	$ catkin_init_workspace

Workspace'iniz boş olsa bile (Başlangıçta ``src`` klasöründe hiç paket yok, sadece ``CMakeLists.txt`` dosyası) workspace'inizi build edebilirsiniz:

::
	
	$ cd ~/catkin_ws/
	$ catkin_make
	$ source devel/setup.bash

Bunları yaptıktan sonra, ``catkin_ws/devel/setup.bash`` dosyanızı öncelikli olarak otomatik source etmek için ``.bashrc`` dosyanızın en altına ekleyin:

::
	
	$ echo "source devel/setup.bash" >> ~/.bashrc