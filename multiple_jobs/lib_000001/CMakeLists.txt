project(lib_000001)

set(lib_000001_SOURCES class_000005.cxx
    class_000006.cxx
    class_000007.cxx
    class_000008.cxx
    class_000009.cxx)

add_library(lib_000001 STATIC ${lib_000001_SOURCES})
