# The inference examples example for Tensorflow Lite.

cmake_minimum_required(VERSION 3.4.1)

PROJECT(inference_tf CXX)

# base Cmake config
# allow gdb debug
set(CMAKE_BUILD_TYPE "Debug")
set(CMAKE_CXX_FLAGS_DEBUG "$ENV{CXXFLAGS} -O0 -Wall -g -ggdb")
set(CMAKE_CXX_FLAGS_RELEASE "$ENV{CXXFLAGS} -O3 -Wall")
 
#add C++11 support and other options
set(CMAKE_CXX_FLAGS "-std=c++14 ${CMAKE_CXX_FLAGS} -g -ftest-coverage -fprofile-arcs -Wno-deprecated")
#set(CMAKE_CXX_FLAGS "-std=c++0x ${CMAKE_CXX_FLAGS -g -ftest-coverage -fprofile-arcs"})

#set(OpenCV_DIR "/usr/local/share/OpenCV")
find_package(OpenCV REQUIRED)

include_directories(
    ${PROJECT_SOURCE_DIR}
    ${OpenCV_INCLUDE_DIRS}
    ${CMAKE_CURRENT_SOURCE_DIR}/include
)

# add_executable
add_executable(lane_detection
    ${CMAKE_CURRENT_SOURCE_DIR}/Lane.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/LaneDetectionModule.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/main.cpp
)

target_link_libraries(lane_detection
    ${OpenCV_LIBS}	
)
