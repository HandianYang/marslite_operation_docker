FROM ros:noetic-ros-base-focal
LABEL maintainer="HandianYang"

ENV DEBIAN_FRONTEND=noninteractive

# Path settings
ARG USERNAME=developer
ENV HOME=/home/${USERNAME}

# Install basic tools, Python, and pip
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
      # Python
      python3-pip \
      python3.8-dev \
      # Basic tools
      curl \
      git \
      gnupg2 \
      lsb-release \
      unzip \
      vim \
      wget && \
    rm -rf /var/lib/apt/lists/*

# Install ROS packages
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
      # controller tools
      ros-${ROS_DISTRO}-moveit \
      ros-${ROS_DISTRO}-ros-controllers \
      # RViz
      ros-${ROS_DISTRO}-rviz \
      # Gazebo
      ros-${ROS_DISTRO}-gazebo-ros-pkgs \
      ros-${ROS_DISTRO}-gazebo-ros-control \
      # marslite robot simulation
      ros-${ROS_DISTRO}-gripper-action-controller \
      ros-${ROS_DISTRO}-hector-models \
      ros-${ROS_DISTRO}-ira-laser-tools \
      ros-${ROS_DISTRO}-joint-trajectory-controller \
      # visualization tools
      ros-${ROS_DISTRO}-moveit-visual-tools \
      ros-${ROS_DISTRO}-rviz-visual-tools \
      # navigation
      ros-${ROS_DISTRO}-amcl \
      ros-${ROS_DISTRO}-dwa-local-planner \
      ros-${ROS_DISTRO}-gmapping \
      ros-${ROS_DISTRO}-map-server \
      ros-${ROS_DISTRO}-move-base \
      ros-${ROS_DISTRO}-move-base-msgs \
      # ros-sharp
      ros-${ROS_DISTRO}-rosbridge-server && \
    rm -rf /var/lib/apt/lists/*

# Copy project files
WORKDIR ${HOME}
COPY . ${HOME}

# Install cartesian controller as ROS workspace
RUN mkdir -p ${HOME}/cartesian_control_ws/src
WORKDIR ${HOME}/cartesian_control_ws/src
RUN apt-get update && \
    git clone --branch ros1 https://github.com/fzi-forschungszentrum-informatik/cartesian_controllers.git && \
    rosdep update && \
    rosdep install --from-paths ./ --ignore-src -y
WORKDIR ${HOME}/cartesian_control_ws
RUN /bin/bash -c "source /opt/ros/noetic/setup.bash && \
    catkin_make -DCMAKE_BUILD_TYPE=Release"

# Set aliases and environment settings in .bashrc
WORKDIR ${HOME}
RUN echo "" >> ${HOME}/.bashrc && \
    echo "source /opt/ros/${ROS_DISTRO}/setup.bash" >> ${HOME}/.bashrc && \
    echo "source /usr/share/gazebo-11/setup.sh" >> ${HOME}/.bashrc && \
    echo "source ${HOME}/cartesian_control_ws/devel/setup.bash" >> ${HOME}/.bashrc && \
    echo "export ROSCONSOLE_FORMAT='[${severity}] [${node}]: ${message}'" >> ${HOME}/.bashrc && \
    echo "" >> ${HOME}/.bashrc && \
    echo "alias cm='catkin_make'" >> ${HOME}/.bashrc && \
    echo "alias sd='source devel/setup.bash'" >> ${HOME}/.bashrc && \
    # aliases for switching between local launch and remote launch
    # [NOTE] change the correct IP of your robot 
    # echo "alias local='export ROS_HOSTNAME=localhost && export ROS_MASTER_URI=http://localhost:11311'" >> ${HOME}/.bashrc && \
    # echo "alias robot='export ROS_MASTER_URI=http://192.168.50.77:11311'" >> ${HOME}/.bashrc && \
    # [NOTE] comment the below line if you don't use my ROS workspace, or
    #        change the path to where your Gazebo model locates
    # echo "export GAZEBO_MODEL_PATH=${CATKIN_WS_PATH}/src/mars_lite_description/models:\$GAZEBO_MODEL_PATH" >> ${HOME}/.bashrc && \
    apt-get clean

# # NVIDIA settings
# ENV NVIDIA_VISIBLE_DEVICES=all
# ENV NVIDIA_DRIVER_CAPABILITIES=compute,utility
