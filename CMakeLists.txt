cmake_minimum_required(VERSION 3.20)

project(turnbinds LANGUAGES CXX RC)

if (MSVC)
    set(CMAKE_GENERATOR_PLATFORM x64)
endif()

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

add_executable(turnbinds
    src/turnbinds.cpp
    src/turnbinds.rc
)

target_compile_definitions(turnbinds PRIVATE
    WIN32_LEAN_AND_MEAN
)

if (MSVC)
    target_compile_options(turnbinds PRIVATE /W3)
endif()
