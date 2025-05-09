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

# Set aliases and environment settings in .bashrc
RUN echo "" >> ${HOME}/.bashrc && \
    echo "source /opt/ros/${ROS_DISTRO}/setup.bash" >> ${HOME}/.bashrc && \
    echo "source /usr/share/gazebo-11/setup.sh" >> ${HOME}/.bashrc && \
    echo "export ROSCONSOLE_FORMAT='[\${severity}] [\${node}]: \${message}'" >> ${HOME}/.bashrc && \
    echo "" >> ${HOME}/.bashrc && \
    echo "alias cm='catkin_make'" >> ${HOME}/.bashrc && \
    echo "alias sd='source devel/setup.bash'" >> ${HOME}/.bashrc && \
    apt-get clean
