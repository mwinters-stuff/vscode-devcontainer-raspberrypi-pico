# vscode-devcontainer-raspberrypi-pico 

## VSCode Dev Container for the Raspberry PI Pico C SDK

## This container includes
* pico-sdk
* pico-extras
* pico-project-generator
* openocd - compiled for picoprobe
* picotool
* bootterm (for serial monitoring) - see https://github.com/wtarreau/bootterm

## Usage

* Clone or download the repository
* Copy the contents of .devcontainer into your project
* Copy the contents of .vscode into your project
* Remove any existing "build" directory.
* Open the folder and allow the container to build.

## To know

* SDK is installed in /apps/pico-sdk
* EXTRAS is installed in /apps/pico-extras
* PICO-PROJECT-GENERATOR is installed in /apps/pico-project-generator
* All USB devices are exported to container - so the picoprobe can be found and used.
* USB Device /dev/ttyACM0 is exported to container for monitoring
