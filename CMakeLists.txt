project(game.libretro.yabause)

cmake_minimum_required(VERSION 2.6)

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR})

find_package(kodi REQUIRED)
find_package(yabause REQUIRED)

set(DEPLIBS yabause)
set(YABAUSE_CUSTOM_BINARY ${YABAUSE_LIB}
                          game.libretro.yabause${CMAKE_SHARED_LIBRARY_SUFFIX} yabause)

build_addon(game.libretro.yabause YABAUSE DEPLIBS)

