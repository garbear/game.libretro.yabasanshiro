project(game.libretro.yabause)

cmake_minimum_required(VERSION 2.6)

find_package(kodi REQUIRED)

include(ExternalProject)
externalproject_add(yabause
                    GIT_REPOSITORY https://github.com/libretro/yabause
                    GIT_TAG 4e47c6c
                    PREFIX yabause
                    CONFIGURE_COMMAND ""
                    INSTALL_COMMAND ""
                    BUILD_COMMAND make -C libretro
                    BUILD_IN_SOURCE 1)

set(YABAUSE_CUSTOM_BINARY ${PROJECT_BINARY_DIR}/yabause/src/yabause/libretro/yabause_libretro${CMAKE_SHARED_LIBRARY_SUFFIX}
                          game.libretro.yabause${CMAKE_SHARED_LIBRARY_SUFFIX} yabause)

build_addon(game.libretro.yabause YABAUSE DEPLIBS)
add_dependencies(game.libretro.yabause yabause)

include(CPack)
