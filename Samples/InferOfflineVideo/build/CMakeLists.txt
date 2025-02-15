cmake_minimum_required(VERSION 2.8)
project(VideoDetection)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 11)

set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})

set(PROJECT_SRC_ROOT ${CMAKE_CURRENT_LIST_DIR}/..)
set(CMAKE_MODULE_PATH ${PROJECT_SRC_ROOT}/../CMake)

file(COPY ${PROJECT_SRC_ROOT}/graph.config
        ${PROJECT_SRC_ROOT}/data/misc/imagenet1000_clsidx_to_labels.txt
        DESTINATION ${CMAKE_BINARY_DIR})

find_package(DDK REQUIRED)
include_directories(${DDK_INCLUDE_DIRS} ${DDK_CEREAL_INCLUDE_DIRS} ${DDK_PROTOBUF_INCLUDE_DIRS})

include_directories(${PROJECT_SRC_ROOT}/include)
include_directories(${PROJECT_SRC_ROOT}/Common)

add_subdirectory(device)
add_subdirectory(host)