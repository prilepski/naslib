cmake_minimum_required(VERSION 2.8.2)

# Defining this project name
project(naslib C CXX)

# Setting where output files to be placed for this project
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_HOME_DIRECTORY}/build)

# Specifying where sade repo is going to be
set(SADE_REPO sade)

# Update submodules (will bring source code for them if necessary)
execute_process(COMMAND git submodule init)
execute_process(COMMAND git submodule update --remote ${SADE_REPO})

# Add "sade" as a project. It will be built before naslib does
add_subdirectory(${SADE_REPO})

# specify include folder from sade to be found by naslib build process
include_directories(${CMAKE_HOME_DIRECTORY}/${SADE_REPO}/include)

# Add all .h and .cpp files into naslib project
file(GLOB naslib_src "*.h" "*.cpp")

# Build naslib executable
add_executable(naslib ${naslib_src})
