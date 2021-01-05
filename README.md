## $5 Tech Unlocked 2021!
[Buy and download this Book for only $5 on PacktPub.com](https://www.packtpub.com/product/effective-robotics-programming-with-ros-third-edition/9781786463654)
-----
*If you have read this book, please leave a review on [Amazon.com](https://www.amazon.com/gp/product/1786463652).     Potential readers can then use your unbiased opinion to help them make purchase decisions. Thank you. The $5 campaign         runs from __December 15th 2020__ to __January 13th 2021.__*

# Effective Robotics Programming with ROS - Third Edition
This is the code repository for [Effective Robotics Programming with ROS - Third Edition](https://www.packtpub.com/hardware-and-creative/effective-robotics-programming-ros-third-edition?utm_source=github&utm_medium=repository&utm_content=9781786463654), published by Packt. It contains all the supporting project files necessary to work through the book from start to finish.
## Instructions and Navigations
All of the code is organized into folders. Each folder starts with a number followed by the application name. For example, B05576_02_Code.

The code will look like the following:
       
        image: map.pgm
        resolution: 0.050000
        origin: [-50.000000, -50.000000, 0.000000]
        negate: 0
        occupied_thresh: 0.65
        free_thresh: 0.196 

### Software requirements:

* Ubuntu 16.04LTS, Ubuntu 16.04 armhf
       
       * ROS Kinetic, Docker, and Virtualbox: http://www.ros.org/
       * ROS Kinetic and Arduino IDE: http://www.arduino.cc/
            
## Related Products:

* [Learning ROS for Robotics Programming - Second Edition]( https://www.packtpub.com/hardware-and-creative/learning-ros-robotics-programming-second-edition?utm_source=github&utm_medium=repository&utm_content=9781783987580 )

* [ROS Robotics By Example]( https://www.packtpub.com/hardware-and-creative/ros-robotics-example?utm_source=github&utm_medium=repository&utm_content=9781782175193 )

* [BeagleBone Robotic Projects]( https://www.packtpub.com/hardware-and-creative/beaglebone-robotic-projects?utm_source=github&utm_medium=repository&utm_content=9781783559329 )

### Note:
Chapter 1 does not have code files.

###Suggestions and Feedback
[Click here] ( https://docs.google.com/forms/d/e/1FAIpQLSe5qwunkGf6PUvzPirPDtuy1Du5Rlzew23UBp2S-P3wB-GcwQ/viewform ) if you have any feedback or suggestions.

## Notes
* The book says "use kinetic" but should work with [Noetic](https://wiki.ros.org/ROS/Installation)
* Follow [Ubuntu installation instructions](https://wiki.ros.org/noetic/Installation/Ubuntu)
* You can run ROS in docker, even with some X11 applications - see https://tuw-cpsg.github.io/tutorials/docker-ros/
* ORB SLAM 2 - possibly a cool ROS library: https://wiki.ros.org/orb_slam2_ros
* Book code: https://github.com/PacktPublishing/Effective-Robotics-Programming-with-ROS

Additional packages needed:
```
sudo apt-get install python3-rosinstall python3-rosdep
sudo apt-get install python-yaml
# To fix some bugs on Ubuntu 20.04
# From https://answers.ros.org/question/39657/importerror-no-module-named-rospkg/?answer=363168#post-id-363168
sudo apt install python-is-python3
# These two packages are for gazebo, installed by default
# sudo apt-get install ros-noetic-gazebo-ros ros-noetic-gazebo-ros-control
# For nanosleep.c - gazebo was throwing error otherwise?
sudo apt install glibc-source
# For robot navigation
sudo apt-get install ros-kinetic-teleop-twist-keyboard
# For fake localization for the Chapter 4 demo
sudo apt-get install ros-noetic-fake-localization ros-noetic-map-server
# For move base msgs
sudo apt install ros-noetic-move-base-msgs ros-noetic-amcl ros-noetic-move-base
```

Creating a workspace:
```
mkdir –p ~/dev/catkin_ws/src
cd ~/dev/catkin_ws/src
catkin_init_workspace
```

Building a package:
```
# Creates package
catkin_create_pkg chapter2_tutorials std_msgs roscpp
# Build package
catkin_make
# To install it, from catkin_ws$
source devel/setup.sh
```

```
# Chapter 4L Incorrect apostrophes around the launch command
roslaunch robot1_gazebo gazebo.launch model:="`rospack find robot1_description`/urdf/robot1_base_03.xacro"
```

To get gazebo with a robot and then sensors (camera/laser):
```
# gazebo (might take a while to start)
roslaunch robot1_gazebo gazebo_wg.launch
# Rviz for visualization
# if you are adding a camera/laser make sure to choose appropriate frame of reference
roslaunch rviz rviz
# For keyboard control of the robot
rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```

```
$ roslaunch chapter5_tutorials gazebo_xacro.launch model:="`rospack find chapter5_tutorials`/urdf/robot1_base_04.xacro"
# includes rviz and a map
$ roslaunch chapter5_tutorials gazebo_mapping_robot.launch model:="`rospack find chapter5_tutorials`/urdf/robot1_base_04.xacro"
$ rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```

### Visual Odometry

* Repo: https://github.com/HKUST-Aerial-Robotics/VINS-Fusion
* Dataset: https://projects.asl.ethz.ch/datasets/doku.php?id=kmavvisualinertialdatasets