cmake_minimum_required(VERSION 3.4)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

project(all)

add_library(formatter STATIC ${CMAKE_CURRENT_SOURCE_DIR}/formatter_lib/formatter.cpp)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/formatter_lib)

add_library(formatter_ex STATIC ${CMAKE_CURRENT_SOURCE_DIR}/formatter_ex_lib/formatter_ex.cpp)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/formatter_ex_lib)

target_link_libraries(formatter_ex formatter)

add_library(solver_lib STATIC ${CMAKE_CURRENT_SOURCE_DIR}/solver_lib/solver.cpp)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/solver_lib)


add_executable(hello_world ${CMAKE_CURRENT_SOURCE_DIR}/hello_world_application/hello_world.cpp) 
target_link_libraries(hello_world formatter_ex)

add_executable(solver ${CMAKE_CURRENT_SOURCE_DIR}/solver_application/equation.cpp)
target_link_libraries(solver formatter_ex)
target_link_libraries(solver solver_lib)