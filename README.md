# vscode-devcontainer-raspberrypi-pico [![Create docker image](https://github.com/mwinters-stuff/vscode-devcontainer-raspberrypi-pico/actions/workflows/build-image.yml/badge.svg)](https://github.com/mwinters-stuff/vscode-devcontainer-raspberrypi-pico/actions/workflows/build-image.yml)
VSCode Dev Container for the Raspberry PI Pico C SDK

## Usage

Clone or download repository, copy the contents of .devcontainer into your project
Remove any existing "build" directory.

Open the folder, and allow the container to build.

# To know
* SDK is installed in /pico-sdk
* All USB devices are exported to container - so the picoprobe can be found and used.
* USB Device /dev/ttyACM0 is exported to container for monitoring

## This container includes
* pico-sdk
* openocd - compiled for picoprobe
* picotool
* bootterm (for serial monitoring) - see https://github.com/wtarreau/bootterm

