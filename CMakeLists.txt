cmake_minimum_required(VERSION 3.10)

# set the project name
project(HelloWorld VERSION 1.0)

# specify the C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

include(FindPkgConfig)

# this projects need opencv4
pkg_check_modules(OPENCV4 REQUIRED opencv4)
include_directories(${OPENCV_INCLUDE_DIRS})
link_directories(${OPENCV_LIBRARY_DIRS})
add_definitions(${OPENCV_CFLAGS_OTHER})

# add the executable
add_executable(hello main.cc)
target_include_directories(hello PUBLIC ${OPENCV4_INCLUDE_DIRS})
target_link_directories(hello PUBLIC ${OPENCV4_LIBRARY_DIRS})
target_link_libraries(hello PUBLIC ${OPENCV4_LIBRARIES})
