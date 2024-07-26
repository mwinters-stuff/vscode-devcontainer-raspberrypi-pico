ARG VARIANT="ubuntu-22.04"
FROM mcr.microsoft.com/vscode/devcontainers/cpp:0-${VARIANT}

ENV TOOLCHAINURL="https://developer.arm.com/-/media/Files/downloads/gnu/13.3.rel1/binrel"
ENV TOOLCHAINARCHIVE="arm-gnu-toolchain-13.3.rel1-x86_64-arm-none-eabi.tar.xz"
ENV TOOLCHAINDIR="arm-gnu-toolchain-13.3.rel1-x86_64-arm-none-eabi"

RUN apt-get update && \
    export DEBIAN_FRONTEND=noninteractive && \
    apt-get -y install --no-install-recommends \
        cmake \
        build-essential \
        wget \
        ca-certificates \
        gdb-multiarch \
        binutils-multiarch \
        automake \
        autoconf \
        libtool \
        libftdi-dev \
        libusb-1.0-0-dev \
        libhidapi-dev \
        pkg-config \
        clang-format \
        python3 \
        python3-tk

WORKDIR /apps

RUN wget $TOOLCHAINURL/$TOOLCHAINARCHIVE 
RUN tar -J --xz  -xf $TOOLCHAINARCHIVE

RUN mv $TOOLCHAINDIR gcc-arm-none && \
    rm $TOOLCHAINARCHIVE 

ENV PATH=$PATH:/apps/gcc-arm-none/bin

RUN cd /apps && \
    git clone -b master https://github.com/raspberrypi/pico-sdk.git --depth=1 && \
    cd pico-sdk && \
    git submodule update --init

ENV PICO_SDK_PATH=/apps/pico-sdk

RUN cd /apps && \
    git clone -b master https://github.com/raspberrypi/pico-extras.git --depth=1 \
    && cd pico-extras && \
    git submodule update --init 

ENV PICO_EXTRAS_PATH=/apps/pico-extras

RUN cd /apps && \
    git clone https://github.com/raspberrypi/pico-project-generator.git

ENV PATH=$PATH:/apps/pico-project-generator

RUN cd /apps && \
    git clone https://github.com/codaris/picovga-cmake.git pico-vga

ENV PICOVGA_PATH=/apps/pico-vga

RUN cd /apps && \
    git clone https://github.com/earlephilhower/arduino-pico.git arduino-pico

ENV ARDUINO_PICO_PATH=/apps/arduino-pico

RUN cd /apps && \
    git clone https://github.com/earlephilhower/ArduinoCore-API.git arduino-core

ENV ARDUINO_CORE_PATH=/apps/arduino-core

RUN git clone https://github.com/raspberrypi/openocd.git --depth=1 && \
    cd openocd && ./bootstrap && ./configure --enable-ftdi --enable-sysfsgpio --enable-picoprobe && make -j 8 install 
RUN cd /apps && git clone https://github.com/raspberrypi/picotool.git --depth=1 && \
    cd picotool && mkdir build && cd build && cmake ../ && make -j 8 && cp picotool /usr/local/bin 
RUN cd /apps && git clone https://github.com/wtarreau/bootterm.git --depth=1 && \
    cd bootterm && make -j 8 install 

RUN cd /usr/bin && ln -s /usr/bin/objdump objdump-multiarch && ln -s /usr/bin/nm nm-multiarch 

RUN usermod -aG plugdev vscode