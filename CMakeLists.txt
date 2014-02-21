project(gameclient.yabause)

cmake_minimum_required(VERSION 2.6)

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR})

enable_language(CXX)

find_package(xbmc REQUIRED)

include(ExternalProject)

externalproject_add(yabause
                    GIT_REPOSITORY https://github.com/libretro/yabause
                    GIT_TAG 214fa4d
                    PREFIX yabause
                    CONFIGURE_COMMAND ""
                    INSTALL_COMMAND ""
                    BUILD_COMMAND make -C libretro
                    BUILD_IN_SOURCE 1)

set(YABAUSE_CUSTOM_BINARY ${PROJECT_BINARY_DIR}/yabause/src/yabause/libretro/libretro${CMAKE_SHARED_LIBRARY_SUFFIX}
                        libretro-yabause${CMAKE_SHARED_LIBRARY_SUFFIX} yabause)

build_addon(gameclient.yabause YABAUSE DEPLIBS)
add_dependencies(gameclient.yabause yabause)
