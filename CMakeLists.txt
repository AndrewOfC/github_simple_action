project(demo)
cmake_minimum_required(VERSION 3.17)

set(CMAKE_CXX_STANDARD 11)

add_subdirectory(lib)

add_executable(demo main.cpp)

target_link_libraries(demo hello)

