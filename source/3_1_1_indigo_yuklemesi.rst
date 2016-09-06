1. Indigo Sürümünün Yüklenmesi
==============================

1.1. Repository'leri ayarlama
-----------------------------

Eğer Ubuntu düzgün yüklenmediyse, ve/veya repo ayarları değişmişse, Ubuntu repository'lerinizi  ``restricted``, ``universe``, ve ``multiverse``'ü destekleyecek şekilde ayarlayın. bunun için `Ubuntu guide(İngilizce) <https://help.ubuntu.com/community/Repositories/Ubuntu>`_ sayfasını izleyebilirsiniz. Eğer düzgün yüklendiyse direk 1.2'ye geçin:

1.2. ``sources.list``'i ayarlama
--------------------------------

Aşağıdaki komutu kopyalayıp şifrenizi girmeniz yeterli;

::
	
	$ sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

1.3. Anahtar verilerini ayarlama
--------------------------------

::
	
	$ sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net --recv-key 0xB01FA116

Eğer ``gpg: keyserver timed out`` ehatasını alıyorsanız, aşağıdaki komutu (yukarıdakinin sonuna ``:80`` eklenmiş halini) deneyebilirsiniz;

::
	
	$ sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116

1.4. Yükleme
------------

Öncelikle debian paket index'lerimizin güncel olduğuna emin olalım;

::
	
	$ sudo apt-get update

Eğer Ubuntu Trusty 14.04.2 sürümünü (14.04.03 de aynı) kullanıyorsanız ve ROS yüklenirken dependency hataları almışsanız, aşağıdaki paketlerin hepsini yüklemeniz gerekebilir.

::
	
	$ sudo apt-get install --install-recommends linux-generic-lts-vivid xserver-xorg-core-lts-vivid xserver-xorg-lts-vivid xserver-xorg-video-all-lts-vivid xserver-xorg-input-all-lts-vivid libwayland-egl1-mesa-lts-vivid libgl1-mesa-glx-lts-vivid libglapi-mesa-lts-vivid libgles1-mesa-lts-vivid libegl1-mesa-lts-vivid xserver-xorg-dev-lts-vivid mesa-common-dev-lts-vivid libxatracker-dev-lts-vivid libgles2-mesa-dev-lts-vivid libgles1-mesa-dev-lts-vivid libgl1-mesa-dev-lts-vivid libgbm-dev-lts-vivid libegl1-mesa-dev-lts-vivid

ROS'da çokca kütüphane ve araç bulunmaktadır. Size başlangıç için 4 farklı seçenek sunulmuştur. Tabi ki zor gelmezse her paketi teker teker de yükleyebilirsiniz. Zor gelirse:

::
	
	$ sudo apt-get install ros-indigo-desktop-full

ve onaylarak, yükleme işleminin bitmesini bekleyin.

1.5. ``rosdep``'i hazırlama
---------------------------

ROS'u kullanmadan önce, ``rosdep``'i hazırlamalısınız. ``rosdep`` kullanacağınız paketler için sistem gereksinimlerini kayıt edilmiş kaynaklardan kolayca yükleyebilmenizi sağlar.

Önce şunu girin;

::
	
	$ sudo rosdep init

bittikten sonra da , bunu;

::
	
	$ rosdep update

1.6. Ortam kurulumu
-------------------

It's convenient if the ROS ortam değişkenlerinin otomatik olarak yüklenmesi için bash'i açarkenki default ayar dosyasına eklenmesi sizin için çok iyidir.

::
	
	$ echo "source /opt/ros/indigo/setup.bash" >> ~/.bashrc

ve terminal'i yeniden açmayacaksanız aşağıdaki komutu girin;

::
	
	$ source ~/.bashrc

Sonrasında her açışınızda otomatik olarak source edilecektir.