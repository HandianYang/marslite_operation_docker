

Version 1.0.0 (May 8, 2025)
----------------------------

+ Built from `ros:noetic-ros-base-focal`
+ Set Python version as 3.8
+ Installed crucial packages:
  - ROS Noetic Moveit!
  - RViz
  - Gazebo 11
  - ROS-sharp (wireless communication for ROS topics)
+ Installed cartesian controller as ROS workspace `cartesian_controller_ws`
+ Added aliases:
  - `cm = catkin_make`
  - `sd = source devel/setup.bash`
+ Set `ROSCONSOLE_FORMAT` as `'[${severity}] [${node}]: ${message}'`