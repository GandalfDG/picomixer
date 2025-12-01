cmake_minimum_required(VERSION 3.13)

include(pico_sdk_import.cmake)

project(picomix C CXX ASM)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)
pico_sdk_init()


add_executable(picomixer
src/picomixer.c
)
pico_generate_pio_header(picomixer ${CMAKE_CURRENT_LIST_DIR}/src/blink.pio ${CMAKE_CURRENT_LIST_DIR}/src/tdm_out.pio)

pico_enable_stdio_usb(picomixer 1)
pico_add_extra_outputs(picomixer)
target_link_libraries(picomixer pico_stdlib hardware_spi hardware_pio hardware_uart)