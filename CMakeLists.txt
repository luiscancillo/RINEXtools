cmake_minimum_required(VERSION 3.21)
project(RINEXtools)

set(CMAKE_CXX_STANDARD 11)
include_directories(../CommonClasses)
#by default, Debug build is assumed
find_library(COMMON_CLASSES CommonClasses PATHS ../CommonClasses/cmake-build-debug)
if (CMAKE_BUILD_TYPE MATCHES Debug)
    message(STATUS ${CMAKE_BUILD_TYPE})
elseif(CMAKE_BUILD_TYPE MATCHES Release)
    message(STATUS ${CMAKE_BUILD_TYPE})
    find_library(COMMON_CLASSES CommonClasses PATHS ../CommonClasses/cmake-build-release)
endif()

add_executable(RINEXtoRINEX RINEXtoRINEX.cpp)
target_link_libraries(RINEXtoRINEX LINK_PUBLIC ${COMMON_CLASSES})
add_executable(RINEXtoCSV RINEXtoCSV.cpp)
target_link_libraries(RINEXtoCSV  ${COMMON_CLASSES})