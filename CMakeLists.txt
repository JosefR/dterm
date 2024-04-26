cmake_minimum_required(VERSION 3.5)

project(dterm LANGUAGES C)

set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED ON)

add_custom_command(
    OUTPUT speeds.h
    COMMAND sh ${CMAKE_SOURCE_DIR}/speeds.sh > speeds.h
)

add_executable(dterm dterm.c speeds.h)
target_include_directories(dterm PRIVATE ${CMAKE_BINARY_DIR})

include(GNUInstallDirs)
install(TARGETS dterm
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)

