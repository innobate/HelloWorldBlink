cmake_minimum_required(VERSION 3.13)
# initialize the board settings, very important for Wifi
set(PICO_BOARD pico_w)

# initialize the SDK based on PICO_SDK_PATH
# note: this must happen before project()
include(pico_sdk_import.cmake)

project(my_project)

# initialize the Raspberry Pi Pico SDK
pico_sdk_init()

# rest of your project
add_executable(hello_world_blink
hello_world_blink.c
)

# Add pico_stdlib library which aggregates commonly used features
target_link_libraries(hello_world_blink pico_stdlib pico_cyw43_arch_none)

# create map/bin/hex/uf2 file in addition to ELF.
pico_add_extra_outputs(hello_world_blink)