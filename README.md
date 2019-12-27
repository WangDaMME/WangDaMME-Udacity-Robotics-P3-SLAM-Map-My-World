# Udacity-Robotics-P4-SLAM-Map-My-World

Mobile Robot - RTAB-Map Graphics SLAM Mapping.

![](workspace/RESULT%20IMAGES/Demo.gif)
![](workspace/RESULT%20IMAGES/RtabMap_DatabaseViewer.PNG)

## Overview
Welcome to Project 4: Map My World! In this project I created a 2D occupancy grid and 3D octomap from a simulated environment using my mobile robot with the RTAB-Map package.

RTAB-Map (Real-Time Appearance-Based Mapping) is a popular solution for SLAM to develop robots that can map environments in 3D. RTAB-Map has good speed and memory management, and it provides custom developed tools for information analysis. Most importantly, the quality of the documentation on ROS Wiki <a href="http://wiki.ros.org/rtabmap_ros" target="_blank">http://wiki.ros.org/rtabmap_ros</a> is very high. Being able to leverage RTAB-Map with the robots will lead to a solid foundation for mapping and localization. For this project we will be using the italic>rtabmap_ros package</italic>, which is a ROS wrapper (API) for interacting with RTAB-Map. Keep this in mind when looking at the relative documentation.
<ul>
  <li>I developed my own package to interface with the rtabmap_ros package.</li>
  <li>I built upon my localization project to make the necessary changes to interface the robot with RTAB-Map. An example of this is the addition of an RGB-D camera.</li>
  <li>All files are in the appropriate places, all links are properly connected, naming is properly setup and topics are correctly mapped. Furthermore, the appropriate launch files are generated to launch the robot and map its surrounding environment.</li>  
  <li>After the robot is successfully launched in the environment, I teleop-ed around the room </li>  
</ul>

#### Integration with RTAB-Map Pacakge
According to the documentation,<a href="http://wiki.ros.org/rtabmap_ros" target="_blank">http://wiki.ros.org/rtabmap_ros</a> the recommended robot configuration requires:
<ul>
<li>A 2D Laser, providing sensor_msgs/LaserScan messages
<li>Odometry sensors, providing nav_msgs/Odometry messages
<li>3D Camera, compatible with openni_launch, openni2_launch or freenect_launch ROS packages. Kinetic RGB-D Camera model is used.
</ul>

#### Rtabmap-databaseviewer



## Directory Structure
```
   .Project1                           # Go Chase It Mobile Robot
    ├── my_robot                       # my_robot package                   
    │   ├── launch                     # launch folder for launch files   
    │   │   ├── robot_description.launch
    │   │   ├── world.launch
    │   ├── meshes                     # meshes folder for sensors
    │   │   ├── hokuyo.dae
    │   ├── urdf                       # urdf folder for xarco files
    │   │   ├── my_robot.gazebo
    │   │   ├── my_robot.xacro
    │   ├── world                      # world folder for world files
    │   │   ├── world.world
    │   ├── CMakeLists.txt             # compiler instructions
    │   ├── package.xml                # package info
    ├── ball_chaser                    # ball_chaser package                   
    │   ├── launch                     # launch folder for launch files   
    │   │   ├── ball_chaser.launch
    │   ├── src                        # source folder for C++ scripts
    │   │   ├── drive_bot.cpp
    │   │   ├── process_images.cpp
    │   ├── srv                        # service folder for ROS services
    │   │   ├── DriveToTarget.srv
    │   ├── CMakeLists.txt             # compiler instructions
    │   ├── package.xml                # package info                  
    └──                              
```

## Launch The Project

  1. Clone/Download this project.
  2. Build the project
```
  $ cd /home/workspace/catkin_ws
  $ catkin_make
```
  3. Launch the robot inside the world
```
  $ cd /home/workspace/catkin_ws/
  $ source devel/setup.bash
  $ roslaunch my_robot world.launch
```
  4. Launch ball_chaser to run drive_bot Node & process_image Node
```
  $ cd /home/workspace/catkin_ws/
  $ source devel/setup.bash
  $ roslaunch ball_chaser ball_chaser.launch
```
  5. Visualize the robot's camera images
```
  $ rosrun rqt_image_view rqt_image_view  
```
