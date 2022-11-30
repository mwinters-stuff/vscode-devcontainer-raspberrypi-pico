# vscode-devcontainer-raspberrypi-pico 

## Usage

Clone or download repository, copy the contents of .devcontainer into your project
Remove any existing "build" directory.

Copy the file https://github.com/raspberrypi/openocd/blob/rp2040/contrib/60-openocd.rules to /etc/udev/rules.d on your host computer and restart udev (systemctl restart udev)

Open the folder, and allow the container to build.

## To know
* SDK is installed in /pico-sdk
* All USB devices are exported to container - so the picoprobe can be found and used.
* USB Device /dev/ttyACM0 is exported to container for monitoring

## To try cmsis-dap for picoprobe
Change the repository for OpenOCD in the Dockerfile, comment out the line that clones from raspberry pi
and comment in the line that clones from openocd

## This container includes
* pico-sdk
* openocd - compiled for picoprobe and cmsis-dap
* picotool
* bootterm (for serial monitoring) - see https://github.com/wtarreau/bootterm

