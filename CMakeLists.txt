cmake_minimum_required(VERSION 3.21)
project(CMakeStarter)

set(CMAKE_CXX_STANDARD 23)
set(COMPILER_FLAGS "-fexceptions")

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} ${COMPILER_FLAGS}")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${COMPILER_FLAGS}")

option(ENABLE_UNIT_TESTS "Enable unit tests" ON)
message(STATUS "Enable testing: ${ENABLE_UNIT_TESTS}")

if (ENABLE_UNIT_TESTS)
    enable_testing()
    file(GLOB_RECURSE TESTS test/*.cpp)
    add_subdirectory(test)
endif ()

file(GLOB_RECURSE SOURCES
        src/*.hpp
        src/*.cpp)
list(REMOVE_ITEM SOURCES "src/main.cpp")

add_executable(CMakeStarter ${SOURCES} src/main.cpp)
