2. Creating Workspace
=====================

Now, you need to create one workspace to create custom applications. Create folder, enter to it, and run ``catkin_init_workspace`` command:

::
	
	$ mkdir -p ~/catkin_ws/src
	$ cd ~/catkin_ws/src
	$ catkin_init_workspace

Even though the workspace is empty (there are no packages in the 'src' folder, just a single ``CMakeLists.txt`` link) you can still "build" the workspace:

::
	
	$ cd ~/catkin_ws/
	$ catkin_make
	$ source devel/setup.bash

After doing that, add source command of ``catkin_ws/devel/setup.bash`` to your ``.bashrc`` file for overlay this workspace on top of your environment.

::
	
	$ echo "source devel/setup.bash" >> ~/.bashrc