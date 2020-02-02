# Minimum version of CMake as required by bsf
cmake_minimum_required (VERSION 3.12.0)
# Name of your project
project (bsfHelloWorld)
# Add necessary compiler flags
if(CMAKE_CXX_COMPILER_ID MATCHES "Clang" OR 
   CMAKE_CXX_COMPILER_ID MATCHES "AppleClang" OR
   CMAKE_CXX_COMPILER_ID MATCHES "GNU")
    add_compile_options(-fno-rtti)
endif()
# Make sure to use the C++14 standard
set(CMAKE_CXX_STANDARD 14)
# Build an executable from the provided C++ files
add_executable(myApp "Main.cpp")
# Path to where you have installed bsf
set(bsf_INSTALL_DIR "/Users/funatsu/lab/bsf_v1.1.0b_osx")
# Let CMake know where to find the Findbsf.cmake file (at current folder)
set(CMAKE_MODULE_PATH "${PROJECT_SOURCE_DIR}")
# Find bsf libraries and headers
find_package(bsf REQUIRED)
# Link bsf library with your application
target_link_libraries(myApp PRIVATE bsf)
