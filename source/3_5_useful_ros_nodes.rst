Some useful ROS Nodes
========================

For more information, you can visit the `ROS Wiki <http://wiki.ros.org>`_

`roslaunch <http://wiki.ros.org/roslaunch>`_
--------------------------------------------

``roslaunch`` is a tool for easily launching multiple ROS nodes locally and remotely via SSH, as well as setting parameters on the Parameter Server. It includes options to automatically respawn processes that have already died. roslaunch takes in one or more XML configuration files (with the ``.launch`` extension) that specify the parameters to set and nodes to launch, as well as the machines that they should be run on.

Many ROS packages come with ``.launch`` files, which you can run with:

::
	
	$ roslaunch package_name file.launch


`rqt_console <http://wiki.ros.org/rqt_console>`_ and `rqt_logger_level <http://wiki.ros.org/rqt_logger_level>`_
---------------------------------------------------------------------------------------------------------------------------------------------------

``rqt_console`` provides a GUI plugin for displaying and filtering ROS messages. And ``rqt_logger_level`` provides a GUI plugin for configuring the logger level of ROS nodes. Also  Opening ``rqt_logger_level`` from another terminal isn't mandatory. There is a button on ``rqt_console`` plugin screen for opening it. Be sure these packages are installed,

::
	
	$ sudo apt-get install ros-indigo-rqt ros-indigo-rqt-common-plugins 

You can open these nodes via these commands:

::
	
	$ rosrun rqt_console rqt_console

::
	
	$ rosrun rqt_logger_level rqt_logger_level

We've previously used the ``ROS_INFO(...)`` function in Publisher - Subscriber Tutorial. ROS Node prints this message if logger level is appropriate with info level. For example, If the level isn't Debug, that ROS Node never prints ``ROS_DEBUG(...)`` messages.

`roswtf <http://wiki.ros.org/roswtf>`_
--------------------------------------

``roswtf`` examines your system to try and find problems. Try this command to examine errors when something is wrong:

::
	
	$ roswtf

`rosbag <http://wiki.ros.org/rosbag>`_
--------------------------------------

This is a set of tools for recording from and playing back to ROS topics. It is intended to be high performance and avoids deserialization and reserialization of the messages.

For trying this command, You can try with the one of the previously explained tutorials; Publisher - Subscriber, Navigation or Simply, You can run the MRP2 robot on the gazebo and drive it for a while. But before driving, run

::
	
	$ mkdir ~/bagfiles

::
	
	$ cd ~/bagfiles

::
	
	$ rosbag record -a

And drive the robot via joystick or ``rqt_robot_steering`` plugin. And turn back to terminal which you've opened and left back. And say ``Ctrl + C`` to kill it. And kill the other ROS nodes. Then relaunch the ``mrp2_gazebo.launch``. And play your data to topics back by entering:

::
	
	$ rosbag play <YOUR_BAG_FILE_NAME.bag>

At once, maximize gazebo window and You will see your robot is moving like in its past...
