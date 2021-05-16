cmake_minimum_required(VERSION 3.10)

get_filename_component(ProjectId ${CMAKE_CURRENT_SOURCE_DIR} NAME)
string(REPLACE " " "_" ProjectId ${ProjectId})
project(${ProjectId})

# Set a default build type if none was specified
set(default_build_type "Release")
if(NOT CMAKE_BUILD_TYPE AND NOT CMAKE_CONFIGURATION_TYPES)
  message(STATUS "Setting build type to '${default_build_type}' as none was specified.")
  set(CMAKE_BUILD_TYPE "${default_build_type}")
endif()

file(GLOB_RECURSE sources RELATIVE ${CMAKE_SOURCE_DIR} "src/*.cpp")
add_executable(${ProjectId} ${sources})
set_property(TARGET ${ProjectId} PROPERTY CXX_STANDARD 17)
include_directories(./include)

add_compile_options(-Wall -Wextra -Wpedantic)

# Example of including external libraries

# find_library(libsdl SDL2 REQUIRED IMPORTED)
# find_library(opengl GL REQUIRED IMPORTED)
# target_link_libraries(${ProjectId} ${libsdl})
# target_link_libraries(${ProjectId} ${opengl})
# set(CMAKE_EXE_LINKER_FLAGS "-Wl,-export-dynamic")
