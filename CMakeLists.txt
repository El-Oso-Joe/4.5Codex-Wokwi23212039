cmake_minimum_required(VERSION 3.13)
project(pico_w_keypad_leds C CXX)

# Documentation-oriented scaffold:
# The source in src/main.cpp is Arduino-style (setup/loop, Keypad.h).
# Build it with Arduino core for RP2040 (e.g., Earle Philhower core) or Wokwi Arduino simulation.
# A native Pico SDK port is intentionally not performed to preserve original behavior.

add_custom_target(info ALL
  COMMAND ${CMAKE_COMMAND} -E echo "Use Arduino RP2040 toolchain to build src/main.cpp"
)
