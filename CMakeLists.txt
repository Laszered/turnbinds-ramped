cmake_minimum_required(VERSION 3.16)

project(turnbinds LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# --------------------------------------------------
# Platform / compiler handling
# --------------------------------------------------

if (MSVC)
    add_compile_definitions(_CRT_SECURE_NO_WARNINGS)
endif()

# --------------------------------------------------
# Sources
# --------------------------------------------------

add_executable(turnbinds
    src/main.cpp
)

# --------------------------------------------------
# Compiler warnings
# --------------------------------------------------

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

# --------------------------------------------------
# Windows-specific settings
# --------------------------------------------------

if (WIN32)
    target_compile_definitions(turnbinds PRIVATE WIN32_LEAN_AND_MEAN)
endif()
