cmake_minimum_required(VERSION 3.5)

project(TestArgus LANGUAGES CXX)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(OpenCV_DIR ${CMAKE_CURRENT_SOURCE_DIR}/opencv450/)
message(STATUS "OpenCV DIR:      ${OpenCV_DIR}")

set(OpenCV_INCLUDE_DIR ${OpenCV_DIR}include)
include_directories(${OpenCV_INCLUDE_DIR})
message(STATUS "OpenCV INCLUDE DIR:      ${OpenCV_INCLUDE_DIR}")

set(OpenCV_LIB_DIR    ${OpenCV_DIR}x64/mingw/bin)    #  ${OpenCV_DIR}x64/mingw/lib)
message(STATUS "OpenCV LIB DIR:      ${OpenCV_LIB_DIR}")

find_package(Qt5Core)

add_executable(TestArgus   main.cpp)

target_link_libraries(TestArgus Qt5::Core)

target_link_libraries(TestArgus ${OpenCV_LIB_DIR}/libopencv_core450.dll)
target_link_libraries(TestArgus ${OpenCV_LIB_DIR}/libopencv_imgcodecs450.dll)
target_link_libraries(TestArgus ${OpenCV_LIB_DIR}/libopencv_imgproc450.dll)

