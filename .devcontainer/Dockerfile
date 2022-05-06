FROM althack/ros2:galactic-dev

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update \
   && apt-get -y install --no-install-recommends \
      usbutils \
      libboost-all-dev \
      libusb-1.0-0-dev \
      ros-galactic-joy\
      ros-galactic-pcl-ros\
   #
   # Clean up
   && apt-get autoremove -y \
   && apt-get clean -y \
   && rm -rf /var/lib/apt/lists/*
ENV DEBIAN_FRONTEND=dialog

# Set up auto-source of workspace for ros user
ARG WORKSPACE
RUN echo "if [ -f ${WORKSPACE}/install/setup.bash ]; then source ${WORKSPACE}/install/setup.bash; fi" >> /home/ros/.bashrc

# Add "ros" user to plugdev group
RUN groupadd -g 1003 archplugdev
RUN usermod -a -G archplugdev ros