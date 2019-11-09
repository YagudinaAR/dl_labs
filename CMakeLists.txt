cmake_minimum_required(VERSION 2.8.11)

if(POLICY CMP0056)
    cmake_policy(SET CMP0056 NEW)
endif()

if("${CMAKE_BUILD_TYPE}" STREQUAL "")
    message(STATUS "CMAKE_BUILD_TYPE is unset, defaulting to Release")
    set(CMAKE_BUILD_TYPE "Release")
endif()

set(PROJECT_NAME "dl_labs")
project(${PROJECT_NAME} C CXX)

list(APPEND CMAKE_MODULE_PATH "${PROJECT_SOURCE_DIR}/cmake")

if(UNIX OR MINGW)
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -std=c99")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
endif()
find_package(Threads REQUIRED)
include("cmake/OpenMP.cmake")

message("${CMAKE_C_FLAGS}")
