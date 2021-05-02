cmake_minimum_required(VERSION 3.13)
# initialize the SDK based on PICO_SDK_PATH
# note: this must happen before project()
include(pico_sdk_import.cmake)
project(gbusb)
 
pico_sdk_init()

add_executable(gbusb)

pico_generate_pio_header(gbusb ${CMAKE_CURRENT_LIST_DIR}/pio/spi.pio)

target_include_directories(gbusb PRIVATE ${CMAKE_CURRENT_LIST_DIR})

target_sources(gbusb PRIVATE
        main.c

        usb_descriptors.c

        # PIO components
        pio/pio_spi.c
        )
        
target_link_libraries(gbusb PRIVATE pico_stdlib hardware_pio tinyusb_device tinyusb_board)
pico_add_extra_outputs(gbusb)

