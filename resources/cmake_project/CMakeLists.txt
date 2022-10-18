cmake_minimum_required(VERSION 3.20)

list(APPEND compile_definitions "-DSNTP_COMP_ROUNDTRIP=1" "-DSNTP_CHECK_RESPONSE=2")

include($ENV{IDF_PATH}/tools/cmake/idf.cmake)
project(libespidf C)

idf_build_process($ENV{IDF_TARGET} SDKCONFIG $ENV{SDKCONFIG} SDKCONFIG_DEFAULTS $ENV{SDKCONFIG_DEFAULTS})
idf_build_get_property(aliases BUILD_COMPONENT_ALIASES)

add_executable(libespidf.elf main.c)
target_link_libraries(libespidf.elf PUBLIC "${aliases}")
idf_build_executable(libespidf.elf)