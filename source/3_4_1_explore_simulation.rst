1. Explore the Simulation World
===============================

Explore the simulation environment from robot's vision and save a map.

1. Start Gazebo Process
-----------------------

Note that, be sure the ``ROS_MASTER_IP`` and ``ROS_HOSTNAME`` variables are empty. For that, you should be check this variables after opening up new terminal, like a described in first tutorial.

If there are already running Gazebo process exists you can pass to second seciton directly but for the easiness for launching with a generated map later, be sure the robot is standing in its first location. If it is not, restart by killing and opening it back, via ``Ctrl+C`` and;

::

    $ roslaunch mrp2_gazebo mrp2_gazebo.launch

command, Or normally start in same way;

::

    $ roslaunch mrp2_gazebo mrp2_gazebo.launch

2. Start Gmapping Process
-------------------------

Now you can open Simultaneous Localization and Mapping (SLAM) application, open another terminal window (*We suggest it as a new terminal tab*):

::

    $ roslaunch mrp2_navigation gmapping_demo.launch

Now, gmapping process is started and the robot is started to create a map and locating itself on it. You can start moving robot via joystick or what you prefer to control as a described in previous tutorial.

3. Visualise Gmapping Process via RViz
--------------------------------------

Gmapping process is running but We need to know actually what is going on. Open up another terminal and type;

::

    $ roslaunch mrp2_viz view_gmapping.launch

Finally, can see a part of our world's 2D map from robot's knowledge. You can control the robot via interactive markers and send a simple goal from RViz. 

.. figure:: _static/gmapping.png
	:align: center
	

If your exploring will done, You can save the map whenever you want, open up new terminal and type;

::

    $ rosrun map_server map_saver -f <PATH TO SAVE ex:/home/gazi/>new_map_1

This command generates two files: ``new_map_1.pgm`` and ``new_map_1.yaml``. You can use these files with ``amcl`` application later. To find out how; proceed the next tutorial.
