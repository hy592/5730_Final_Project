add_executable(final_project)

# must match with pio filename and executable name from above
pico_generate_pio_header(final_project ${CMAKE_CURRENT_LIST_DIR}/hsync.pio)
pico_generate_pio_header(final_project ${CMAKE_CURRENT_LIST_DIR}/vsync.pio)
pico_generate_pio_header(final_project ${CMAKE_CURRENT_LIST_DIR}/rgb.pio)

# must match with executable name and source file names
target_sources(final_project PRIVATE final_demo.c vga_graphics.c)

# Add pico_multicore which is required for multicore functionality
target_link_libraries(final_project pico_stdlib pico_bootsel_via_double_reset pico_multicore hardware_pwm hardware_dma hardware_irq hardware_adc hardware_pio hardware_i2c)

# create map/bin/hex file etc.
pico_add_extra_outputs(final_project)