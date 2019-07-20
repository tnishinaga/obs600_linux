FROM debian:buster

RUN apt-get update \
    && apt-get -y install \
        build-essential \
        git \
        bison \
        flex \
        libncurses-dev \
        bc \
        libssl-dev \
        cpio \
        u-boot-tools \
        kmod \
        file \
        curl \
        wget \
        device-tree-compiler \
        binutils-powerpc-linux-gnu \
        gcc-powerpc-linux-gnu \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /root/