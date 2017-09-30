cmake_minimum_required(VERSION 2.8.2)

project(naslib C CXX)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_HOME_DIRECTORY}/build)

include_directories(${CMAKE_HOME_DIRECTORY}/include)

file(GLOB naslib_src "*.h" "*.cpp")
add_executable(naslib ${naslib_src})
