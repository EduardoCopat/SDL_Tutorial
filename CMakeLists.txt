cmake_minimum_required(VERSION 3.12)
project(SDL_Tutorial)

set(CMAKE_CXX_STANDARD 17)

### BEGIN SDL
# https://ccavusoglu.github.io/posts/Setting-up-SDL2-and-SDL_gpu-on-Windows-using-CMake/
set(SDL2_INCLUDE_DIRS ${CMAKE_CURRENT_SOURCE_DIR}/lib/SDL2-2.0.9/i686-w64-mingw32/include)
set(SDL2_PATH ${CMAKE_CURRENT_SOURCE_DIR}/lib/SDL2-2.0.9/i686-w64-mingw32)
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_CURRENT_SOURCE_DIR}/lib")

# Find the SDL2 library
find_package(SDL2 REQUIRED)

# SDL2_INCLUDE_DIR variable set by the FindSDL2 module (if it finds directory).
include_directories(${SDL2_INCLUDE_DIR} ${SDL2_GPU_INCLUDE_PATH})

# Copies SDL2 DLL to build
configure_file("${PROJECT_SOURCE_DIR}/lib/SDL2-2.0.9/i686-w64-mingw32/bin/SDL2.dll" SDL2.dll COPYONLY)

### END SDL

configure_file(hello_world.bmp hello_world.bmp COPYONLY)

add_executable(SDL_Tutorial main.cpp)
target_link_libraries(SDL_Tutorial ${SDL2_LIBRARY} mingw32  )


