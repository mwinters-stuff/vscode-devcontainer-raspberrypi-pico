# vscode-devcontainer-raspberrypi-pico 

## VSCode Dev Container for the Raspberry PI Pico C SDK

## This container includes

* pico-sdk
* pico-extras
* pico-project-generator
* pico-vga
* arduino-pico
* arduino-core
* openocd - compiled for picoprobe
* arduino libraries
* picotool
* bootterm (for serial monitoring) - see https://github.com/wtarreau/bootterm

## Usage

**For an existing project**

* Clone or download the repository
* Copy the contents of .devcontainer into your project
* Copy the contents of .vscode into your project
* Remove any existing "build" directory.
* Open the folder in VSCode and allow the container to build.

**For a new project**

* Create the folder where you want to create the project.
* Copy the contents of .devcontainer into your project
* Copy the contents of .vscode into your project
* Open the folder in VSCode.  When prompted reopen the folder in the container.
* Open a terminal in the dev container and execute the command "pico_project.py --gui".
* Change the project name to the name of your folder.  Change the location to "/workspaces".
* Configure the rest of the project as desired but do not select Create VSCode project under the IDE options.  
* Click OK to generate the code.
* Click Quit to exit the code generator.

**Build and debug the project**

* In the VSCode project Explorer pane, delete the project's build folder.
* In the VSCode left hand pane, select the Run and Debug icon
* In VSCode, press <CTRL><SHIFT>P and select the command CMake: Select a Kit
* Select the GCC 10.3.1 arm-none-eabi compiler.
* In VSCode, press <CTRL><SHIFT>P and select the command CMake: Select a Variant
* Select the Debug variant
* At the top of the screen in the Run and Debug dropdown select Cortext Debug
* Click the green arrow.  If prompted to select a launch target select your project.
* The project will build and run in the debugger.

## Environment Variables

* PICO_SDK_PATH=/apps/pico-sdk
* PICO_EXTRAS_PATH=/apps/pico-extras
* PICOVGA_PATH=/apps/pico-vga
* ARDUINO_PICO_PATH=/apps/arduino-pico
* ARDUINO_CORE_PATH=/apps/arduino-core

## To know

* SDK is installed in /apps/pico-sdk
* EXTRAS is installed in /apps/pico-extras
* PICO-PROJECT-GENERATOR is installed in /apps/pico-project-generator
* PICO-VGA is installed in /apps/pico-vga
* Arduino pico libraries are available in /apps/arduino-pico
* Arduino core libraries are available in /apps/arduino-core
* All USB devices are exported to container - so the picoprobe can be found and used.
* USB Device /dev/ttyACM0 is exported to container for monitoring
