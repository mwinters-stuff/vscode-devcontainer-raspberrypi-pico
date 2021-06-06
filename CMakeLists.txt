# Generated Cmake Pico project file

cmake_minimum_required(VERSION 3.13)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# initalize pico_sdk from installed location
# (note this can come from environment, CMake cache etc)
# set(PICO_SDK_PATH "/home/mathew/src/pico/pico-sdk")

# Pull in Raspberry Pi Pico SDK (must be before project)
include(pico_sdk_import.cmake)

project(TestProject C CXX ASM)

set(PICO_CXX_ENABLE_EXCEPTIONS 1)

# Initialise the Raspberry Pi Pico SDK
pico_sdk_init()

# Add executable. Default name is the project name, version 0.1

add_executable(TestProject TestProject.cpp )

pico_set_program_name(TestProject "TestProject")
pico_set_program_version(TestProject "0.1")

pico_enable_stdio_uart(TestProject 1)
pico_enable_stdio_usb(TestProject 0)

# Add the standard library to the build
target_link_libraries(TestProject pico_stdlib)

# Add any user requested libraries
target_link_libraries(TestProject
        hardware_spi
        hardware_i2c
        hardware_dma
        hardware_clocks
        )

pico_add_extra_outputs(TestProject)

