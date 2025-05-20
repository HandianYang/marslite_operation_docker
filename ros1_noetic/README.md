# `marslite_operation:ros1-noetic`

## Base image: `ubuntu:focal`

## Crucial packages
* ROS Noetic
* ROS Noetic Moveit!
* RViz
* Gazebo 11

## Tools and dependencies
* Common tools
  - `build-essential`
  - `curl`
  - `git`
  - `gnupg2`
  - `lsb-release`
  - `sudo`
  - `unzip`
  - `vim`
  - `wget`
* Python3.8 tools
  - `python3.8-dev`
  - `python3-pip`
* Dependencies for ROS building packages
  - `python3-rosdep`
  - `python3-rosinstall`
  - `python3-rosinstall-generator`
  - `python3-wstool`
* Dependencies for marslite robot simulation
  - `ros-${ROS_DISTRO}-gripper-action-controller`
  - `ros-${ROS_DISTRO}-hector-models`
  - `ros-${ROS_DISTRO}-ira-laser-tools`
  - `ros-${ROS_DISTRO}-joint-trajectory-controller`
* Dependencies for visualization
  - `ros-${ROS_DISTRO}-moveit-visual-tools`
  - `ros-${ROS_DISTRO}-rviz-visual-tools`
* Dependencies for navigation and localization
  - `ros-${ROS_DISTRO}-amcl`
  - `ros-${ROS_DISTRO}-dwa-local-planner`
  - `ros-${ROS_DISTRO}-gmapping`
  - `ros-${ROS_DISTRO}-map-server`
  - `ros-${ROS_DISTRO}-move-base`
  - `ros-${ROS_DISTRO}-move-base-msgs`
* ROS-sharp
  - `ros-${ROS_DISTRO}-rosbridge-server`

## Other features

### Environmental variables
* `ROSCONSOLE_FORMAT: '[${severity}] [${node}]: ${message}'`

### Aliases
* `cm`: `catkin_make`
* `sd`: `source devel/setup.bash`