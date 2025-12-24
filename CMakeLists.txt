cmake_minimum_required(VERSION 3.16)

project(turnbinds LANGUAGES CXX RC)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

add_executable(turnbinds
    src/turnbinds.cpp
    src/turnbinds.rc
)

if (WIN32)
    target_compile_definitions(turnbinds PRIVATE
        WIN32_LEAN_AND_MEAN
        _CRT_SECURE_NO_WARNINGS
        _AMD64_
    )
endif()

if (MSVC)
    target_compile_options(turnbinds PRIVATE /W4)
else()
    target_compile_options(turnbinds PRIVATE
        -Wall
        -Wextra
        -Werror
        -Wno-switch
        -Wno-vla-cxx-extension
    )
endif()
