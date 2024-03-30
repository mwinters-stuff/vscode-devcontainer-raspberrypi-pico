# vscode-devcontainer-raspberrypi-pico 

## VSCode Dev Container for the Raspberry PI Pico C SDK

## This container includes

* pico-sdk
* pico-extras
* pico-project-generator
* pico-vga
* openocd - compiled for picoprobe
* picotool
* bootterm (for serial monitoring) - see https://github.com/wtarreau/bootterm

## Usage

**For an existing project**

* Clone or download the repository
* Copy the contents of .devcontainer into your project
* Copy the contents of .vscode into your project
* Remove any existing "build" directory.
* Open the folder and allow the container to build.

**For a new project**

* Open the folder where you want to create the project in the dev container.
* Open a terminal in the dev container and execute the command "pico_project.py --gui".
* Configure the project but do not select Create VSCode project under the IDE options.  
* Click OK to generate the code.
* Click Quit to exit the code generator.
* Copy the .devcontainer folder from the dev container repository to the project folder.
* Copy the .vscode folder from the dev container repository to the project folder.
* In VSCode, select File > Open Folder and select the project folder.  
* Click OK and open the project in the dev container.

**Confirm you can build and debug the project**

* In VSCode, open the Settings menu (\<CTRL\>\<SHIFT\>P) and choose CMake: Select a Kit.  
* Chose the arm-none-eabi compiler.
* Build the executable as normal.
* You can now debug the executable using the Run and Debug extension.

## Environment Variables

* PICO_SDK_PATH=/apps/pico-sdk
* PICO_EXTRAS_PATH=/apps/pico-extras
* PICOVGA_PATH=/apps/pico-vga

## To know

* SDK is installed in /apps/pico-sdk
* EXTRAS is installed in /apps/pico-extras
* PICO-PROJECT-GENERATOR is installed in /apps/pico-project-generator
* PICO-VGA is installed in /apps/pico-vga
* All USB devices are exported to container - so the picoprobe can be found and used.
* USB Device /dev/ttyACM0 is exported to container for monitoring
