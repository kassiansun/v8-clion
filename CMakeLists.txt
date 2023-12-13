cmake_minimum_required(VERSION 3.26)
project(v8)

set(CMAKE_CXX_STANDARD 20)
add_definitions(-DV8_COMPRESS_POINTERS=1)
add_definitions(-DV8_31BIT_SMIS_ON_64BIT_ARCH=1)
add_definitions(-DV8_ENABLE_SANDBOX)
file(GLOB_RECURSE V8_LIB # just GLOB is probably fine
       "/opt/homebrew/opt/v8/*.dylib"
)
include_directories(
        /opt/homebrew/opt/v8/include
)

add_executable(v8 main.cpp)
target_link_libraries(v8 LINK_PUBLIC ${V8_LIB})
