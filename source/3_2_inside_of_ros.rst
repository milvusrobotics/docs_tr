4. What's working inside of ROS?
================================

As a described in How ROS works part under the Introducing section; Nodes, Topics and parameters are the some of most important parts of ROS. 

For this tutorial, First, run MRP2 on gazebo:

::
	
	$ roslaunch mrp2_gazebo mrp2_gazebo.launch

and minimize it. That launch file starts roscore and some nodes and some topics.


4.1 Nodes
---------

As a described previously, a node really isn't much more than an executable file within a ROS package.

To run another node by hand, you can use rosrun command. For example, if you haven't joystick controller or you have a joystick controller but if you want to some chaos on robot's control, open up another terminal run ``rqt_robot_steering``:

::
	
	$ rosrun rqt_robot_steering rqt_robot_steering

Now you can send the velocity commands to robot with that robot steering window if the topics name in box is correct. Open up another terminal or terminal tab and enter this to list a running nodes:

::
	
	$ rosnode list

This command prints list of the ROS nodes that are currently running. You can find your previously runned robot steering node. Also type just single rosnode command to see simple help:

::
	
	$ rosnode

And take a look at the rosnode usage examples.


4.2 Topics
----------

Topics are named buses over which nodes exchange messages. As a mentioned under the Nodes Section, You must provide topics to nodes for their communication. To see current connection between nodes, enter:

::
	
	$ rosrun rqt_graph rqt_graph

You will see the graph of all running nodes an topics. Now, we can see which datas are transferring between the nodes over topics. To see list of al topics, enter:

::
	
	$ rostopic list

Then choose one of them. Our choice is odometry topic. This topic is published by gazebo, in a real robot, the robot hardware reads from sensors and publishes it. To see the robot's odometry information, enter:

::
	
	$ rostopic echo /mobile_base_controller/odom

Also type just single rostopic command to see simple help:

::
	
	$ rostopic

And take a look at the rostopic usage examples.


4.3 Messages
------------

Messages can include arbitrarily nested structures and arrays (much like C structs).

To see odometry topic's message type, enter:

::
	
	$ rostopic type /mobile_base_controller/odom

The output will equal to ``nav_msgs/Odometry``. 

And to see the message's content use ``rosmsg`` command:

::
	
	$ rosmsg show nav_msgs/Odometry

The output will be contained some other message types. Because some ROS messages contains  other message types for using in easy way.

4.4 Parameters
--------------

A parameter server is a shared, multi-variate dictionary that is accessible via network  APIs. Nodes use this server to store and retrieve parameters at runtime. As it is not designed for high-performance, it is best used for static, non-binary data such as configuration parameters.

And the ``rosparam`` command-line tool can get and set ROS Parameters on the Parameter Server using YAML-encoded files. It also contains an experimental library for using YAML with the Parameter Server. This library is intended for internal use only. ``rosparam`` can be invoked within a roslaunch file.

For listing all parameters, use:

::
	
	$ rosparam list

command. If you've not closed roscore process, parameter server keeps the parameters. But if the starting node sets the parameter at the starting, the value can change.

If you've not closed a running robot on gazebo process, continue, Otherwise reopen like a described in above.

You can print and change parameters via ``rosparam get`` / ``rosparam set`` commands. You can see all parameters' names by typing:

::
	
	$ rosparam list

To read value of any parameter, select one of them of output lines of above command, and replace ``<PARAMETER_NAME>`` with it below:

::
	
	$ rosparam get PARAMETER_NAME

Also, to ``set``:

::
	
	$ rosparam set PARAMETER_NAME NEW_VALUE















