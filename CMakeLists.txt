cmake_minimum_required(VERSION 3.14)
project(a)

set(CMAKE_CXX_STANDARD 14)

include(FetchContent)
FetchContent_Declare(b
        GIT_REPOSITORY https://github.com/pjknowles/b)
FetchContent_Populate(b)
message(b_SOURCE_DIR:${b_SOURCE_DIR})
add_subdirectory(${b_SOURCE_DIR} ${b_BINARY_DIR})

add_executable(a main.cpp)
target_include_directories(a PRIVATE ${b_SOURCE_DIR})
target_link_libraries(a PRIVATE b)
