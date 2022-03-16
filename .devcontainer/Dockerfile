FROM althack/ros2:foxy-dev

# RUN apt-get update && apt-get install -y \
#     ros-foxy-turtlesim \
#     && rm -rf /var/lib/apt/lists/*

RUN apt-get update && apt-get install -y \
    vim  ~nros-foxy-rqt* libqt5gui5 ros-foxy-plotjuggler-ros\
    && rm -rf /var/lib/apt/lists/*


# Setting users password 
USER root
RUN echo "root:root" | chpasswd
RUN echo "ros:root" | chpasswd

ENV QT_DEBUG_PLUGINS=1


RUN apt-get update && apt-get install -y \
    mesa-utils libgl1-mesa-glx xserver-xorg-video-all \
    && rm -rf /var/lib/apt/lists/*

RUN apt-get update && apt-get install -y \
    curl libcurl4 libgl1-mesa-dev libsm6 libice6 libxext6 libxrender1 libdbus-1-3 libvips-dev xorg libx11-dev libglu1-mesa-dev libfreetype6-dev freeglut3 freeglut3-dev mesa-common-dev libglew1.5-dev libglm-dev mesa-utils libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core \
    && rm -rf /var/lib/apt/lists/*

RUN apt-get update && apt-get install -y \
    qt5-default \
    && rm -rf /var/lib/apt/lists/*

ENV NVIDIA_VISIBLE_DEVICES all
ENV NVIDIA_DRIVER_CAPABILITIES graphics,utility,compute 


# Choose to run as user
ENV USER ros
# Change HOME environment variable
USER ros 
# workspace setup
ENV HOME /home/${USER} 
RUN mkdir -p ${HOME}/ros_ws/src

WORKDIR ${HOME}/ros_ws/src
RUN /bin/bash -c "source /opt/ros/${ROS_DISTRO}/setup.bash"

WORKDIR ${HOME}/ros_ws 
RUN /bin/bash -c "source /opt/ros/${ROS_DISTRO}/setup.bash;"

RUN colcon build 

# Adding all the necessary ros sourcing
RUN echo "" >> ~/.bashrc
RUN echo "## ROS" >> ~/.bashrc
RUN echo "source /opt/ros/$ROS_DISTRO/setup.bash" >> ~/.bashrc
RUN echo "source /home/ros/ros_ws/install/setup.bash" >> ~/.bashrc

ENV QT_SELECTION=/usr/bin/qmake


# USER root


# USER ros
