FROM px4io/px4-dev:v1.16.0

ARG DEBIAN_FRONTEND=noninteractive

WORKDIR /workspace

RUN apt-get update && apt-get install -y --no-install-recommends \
    curl \
    nano \
    lsb-release \
    gnupg

# Gazebo
RUN curl https://packages.osrfoundation.org/gazebo.gpg --output /usr/share/keyrings/pkgs-osrf-archive-keyring.gpg
RUN echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/pkgs-osrf-archive-keyring.gpg] https://packages.osrfoundation.org/gazebo/ubuntu-stable $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/gazebo-stable.list > /dev/null
RUN apt-get update && apt-get install gz-harmonic -y

RUN add-apt-repository -y universe && \
	apt-get update && apt-get install -y \
	libopencv-dev \
	python3-opencv \
	libgstreamer1.0-dev \
	libgstreamer-plugins-base1.0-dev \
	default-jdk


RUN rm -rf /var/lib/apt/lists/*
