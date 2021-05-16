project(lib_000000)

set(lib_000000_SOURCES class_000000.cxx
    class_000001.cxx
    class_000002.cxx
    class_000003.cxx
    class_000004.cxx)

add_library(lib_000000 STATIC ${lib_000000_SOURCES})
