# gb-link-firmware
## How to build
### Get the code
Clone the gb-link-firmware repo using `git clone https://github.com/stacksmashing/gb-link-firmware.git` and get a copy of the pico-sdk using `git clone https://github.com/raspberrypi/pico-sdk`.

In order to include the tinyusb source make sure to run `git submodule update --init` inside `./pico-sdk`.

### Set up the pico-sdk depedencies
For Ubuntu use 

`sudo apt install cmake gcc-arm-none-eabi libnewlib-arm-none-eabi libstdc++-arm-none-eabi-newlib`

and make sure to check the [official repo](https://github.com/raspberrypi/pico-sdk) for changes.

Then copy `./pico-sdk/external/pico_sdk_import.cmake` into `./gb-link-firmware/` and make sure to set `PICO_SDK_PATH` to the location of the pic-sdk folder.

### Set up build folder
Inside `gb-link-firmware` create an `build` folder. If you made changes to the location of `pico-sdk`, the environment variable or similiar it is often easier to clean the content of this folder to make sure changes got pick up.

### Actually compile something
Inside `gb-link-firmware` run both `cmake ..` and `make` in order to get your firmware build.

If you made no changes to the make file the firmware should be generated as `gbusb.uf2`.