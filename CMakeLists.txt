cmake_minimum_required(VERSION 3.1)
project(game.libretro.yabause)

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR})

find_package(Kodi REQUIRED)
find_library(YABAUSE_LIB NAMES yabause_libretro${CMAKE_SHARED_LIBRARY_SUFFIX} PATH_SUFFIXES libretro)

set(YABAUSE_CUSTOM_BINARY ${YABAUSE_LIB}
    ${PROJECT_NAME}${CMAKE_SHARED_LIBRARY_SUFFIX})

build_addon(${PROJECT_NAME} YABAUSE "")

include(CPack)
