cmake_minimum_required(VERSION 2.8.7)

#set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14")

add_subdirectory(modules)

set(QUANDLCPP_INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/quandlcpp/include/ CACHE INTERNAL "")
set(QUANDLCPP_LIB quandlcpp CACHE INTERNAL "")

#include_directories(${PROJECT_SOURCE_DIR}/quandlcpp/include/)
include_directories(${QUANDLCPP_INCLUDE_DIR})
include_directories(${CPR_INCLUDE_DIRS})
include_directories(${JSON_INCLUDE_DIRS})

set(QUANDLCPP_FILES
        quandlcpp/src/stock.cpp 
        quandlcpp/src/quandl/quandl.cpp
        quandlcpp/src/quandl/databases/database.cpp 
        quandlcpp/src/quandl/response.cpp
        )
        
add_library(quandlcpp ${QUANDLCPP_FILES})
target_link_libraries(quandlcpp ${CPR_LIBRARIES})