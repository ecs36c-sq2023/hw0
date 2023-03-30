cmake_minimum_required(VERSION 3.22)
# Updated to 3.22 to match the cmake version on CSIF
# Defines the minimum required cmake version
# You can check cmake version on your os by typing 
# `cmake --version` on the terminal

project(hw0 VERSION 1.1.0)
# Project Name and Version

add_subdirectory(src)
# There is a `src` folder in the current directory
# this runs the setting from `src/CMakeLists.txt`

add_executable(main main.cpp)

target_link_libraries(main PUBLIC insertion_sort)
# Links insertion_sort library to main
