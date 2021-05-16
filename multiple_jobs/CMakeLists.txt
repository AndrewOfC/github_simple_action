project(demo)
cmake_minimum_required(VERSION 3.16)

set(CMAKE_CXX_STANDARD 11)

add_subdirectory(lib_000000)
add_subdirectory(lib_000001)
add_subdirectory(lib_000002)
add_subdirectory(lib_000003)
add_subdirectory(lib_000004)


add_executable(demo main.cxx)

target_link_libraries(demo 
lib_000000
lib_000001
lib_000002
lib_000003
lib_000004
)
