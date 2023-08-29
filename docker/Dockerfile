FROM debian:bullseye

RUN dpkg --add-architecture armhf

RUN apt-get update && apt-get install -y \
    autogen \
    automake \
    bash \
    bc \
    bison \
    build-essential \
    bzip2 \
    ca-certificates \
    ccache \
    chrpath \
    cmake \
    cpio \
    curl \
    diffstat \
    fakeroot \
    file \
    flex \
    gawk \
    gcc-arm-linux-gnueabihf \
    g++-arm-linux-gnueabihf \
    git \
    gzip \
    kmod \
    libgpiod-dev:armhf \
    libncursesw5-dev \
    libssl-dev \
    libtool \
    locales \
    lzop \
    make \
    multistrap \
    ncurses-dev \
    pkg-config \
    python \
    python3 \
    python3-pip \
    python3-pexpect \
    qemu-user-static \
    rsync \
    socat \
    runit \
    texinfo \
    u-boot-tools \
    unzip \
    vim \
    wget \
    xz-utils

# To make a more readable PS1 to show we are in the Docker
ENV debian_chroot debian_bullseye
RUN echo "PS1='\${debian_chroot}\\[\033[01;32m\\]@\\H\[\\033[00m\\]:\\[\\033[01;34m\\]\\w\\[\\033[00m\\]\\$ '" >> /etc/bash.bashrc

# Set up locales.  Needed by yocto.
RUN sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen && \
        echo 'LANG="en_US.UTF-8"'>/etc/default/locale && \
        dpkg-reconfigure --frontend=noninteractive locales && \
        update-locale LANG=en_US.UTF-8

ENV LC_ALL en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US.UTF-8

WORKDIR /home/
ADD dune dune/

RUN mkdir -p /home/build/