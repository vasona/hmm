cmake_minimum_required(VERSION 3.18)
project(hmm CXX)

set (SRC
    include/hmm/base.h
    include/hmm/blur.h
    include/hmm/heightmap.h
    include/hmm/stb_image_write.h
    include/hmm/stb_image.h
    include/hmm/stl.h
    include/hmm/triangulator.h
    src/base.cpp
    src/blur.cpp
    src/heightmap.cpp
    src/stl.cpp
    src/triangulator.cpp
)

add_compile_options(-fcolor-diagnostics)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

add_subdirectory(glm)

add_library(hmm SHARED ${SRC})
set_property(TARGET hmm PROPERTY CXX_STANDARD 20)
target_link_libraries(hmm PRIVATE glm)
target_include_directories(hmm PUBLIC include)
