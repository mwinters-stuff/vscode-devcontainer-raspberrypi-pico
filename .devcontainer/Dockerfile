# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.177.0/containers/cpp/.devcontainer/base.Dockerfile

# [Choice] Debian / Ubuntu version: debian-10, debian-9, ubuntu-20.04, ubuntu-18.04
ARG VARIANT="ubuntu-20.04"
FROM mcr.microsoft.com/vscode/devcontainers/cpp:0-${VARIANT}

# [Optional] Uncomment this section to install additional packages.
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends cmake build-essential wget ca-certificates \
    gdb-multiarch automake autoconf libtool libftdi-dev libusb-1.0-0-dev pkg-config clang-format
WORKDIR /apps
RUN wget https://developer.arm.com/-/media/Files/downloads/gnu-rm/10.3-2021.10/gcc-arm-none-eabi-10.3-2021.10-x86_64-linux.tar.bz2 && \
    tar xjf gcc-arm-none-eabi-10.3-2021.10-x86_64-linux.tar.bz2 
RUN mv gcc-arm-none-eabi-10.3-2021.10 gcc-arm-none && \
    rm gcc-arm-none-eabi-10.3-2021.10-x86_64-linux.tar.bz2 
ENV PATH=$PATH:/apps/gcc-arm-none/bin
RUN git clone -b master https://github.com/raspberrypi/pico-sdk.git --depth=1 && cd pico-sdk && git submodule update --init 
ENV PICO_SDK_PATH=/apps/pico-sdk
RUN git clone https://github.com/raspberrypi/openocd.git -b picoprobe --depth=1 \
    && cd openocd && ./bootstrap && ./configure --enable-ftdi --enable-sysfsgpio --enable-picoprobe && make -j 8 install \
    && cd /apps && git clone https://github.com/raspberrypi/picotool.git --depth=1 \
    && cd picotool && mkdir build && cd build && cmake ../ && make -j 8 && cp picotool /usr/local/bin \
    && cd /apps && git clone https://github.com/wtarreau/bootterm.git --depth=1 \
    && cd bootterm && make -j 8 install 
