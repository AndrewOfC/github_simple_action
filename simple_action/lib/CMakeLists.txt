project(hellolib)

set(lib_SOURCES sayhello.cpp)

add_library(hello STATIC ${lib_SOURCES})
