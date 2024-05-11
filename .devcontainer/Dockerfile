ARG VARIANT="ubuntu-20.04"
FROM mcr.microsoft.com/vscode/devcontainers/cpp:0-${VARIANT}

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
        pkg-config \
        clang-format \
        python3 \
        python3-tk
WORKDIR /apps
RUN wget https://developer.arm.com/-/media/Files/downloads/gnu-rm/10.3-2021.10/gcc-arm-none-eabi-10.3-2021.10-x86_64-linux.tar.bz2 && \ 
    tar xjf gcc-arm-none-eabi-10.3-2021.10-x86_64-linux.tar.bz2 
RUN mv gcc-arm-none-eabi-10.3-2021.10 gcc-arm-none && \
    ln -s /apps/gcc-arm-none/bin/arm-none-eabi-gcc /usr/bin/arm-none-eabi-gcc && \
    rm gcc-arm-none-eabi-10.3-2021.10-x86_64-linux.tar.bz2 
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
RUN git clone https://github.com/raspberrypi/openocd.git -b picoprobe --depth=1 && \
    cd openocd && ./bootstrap && ./configure --enable-ftdi --enable-sysfsgpio --enable-picoprobe && make -j 8 install && \
    cd /apps && git clone https://github.com/raspberrypi/picotool.git --depth=1 && \
    cd picotool && mkdir build && cd build && cmake ../ && make -j 8 && cp picotool /usr/local/bin && \
    cd /apps && git clone https://github.com/wtarreau/bootterm.git --depth=1 && \
    cd bootterm && make -j 8 install 
RUN cd /usr/bin && ln -s /usr/bin/objdump objdump-multiarch && ln -s /usr/bin/nm nm-multiarch 
