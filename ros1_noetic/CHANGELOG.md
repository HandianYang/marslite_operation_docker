Version 1.1.0 (May 20, 2025)
----------------------------

+ Major bugfix: cannot build `mars_lite_remote_ws` ROS workspace 
+ Rebuilt image from `ubuntu:focal`
+ Installed ROS Noetic manually

Version 1.0.0 (May 8, 2025)
----------------------------

+ Built from `ros:noetic-ros-base-focal`
+ Set Python version as 3.8
+ Installed crucial packages:
  - ROS Noetic Moveit!
  - RViz
  - Gazebo 11
  - ROS-sharp (wireless communication for ROS topics)
+ Added aliases:
  - `cm = catkin_make`
  - `sd = source devel/setup.bash`
+ Set `ROSCONSOLE_FORMAT` as `'[${severity}] [${node}]: ${message}'`