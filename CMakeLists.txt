
cmake_minimum_required(VERSION 3.10)

project(fizmo
  LANGUAGES C
  DESCRIPTION "fizmo z-machine interpreter"
  VERSION 0.9.0)

#option(BUILD_SUBPROJECT_X "Enable building X" ON)

#set(SUBPROJECT_INSTALL_PREFIX "${CMAKE_CURRENT_SOURCE_DIR}/install" CACHE STRING "project")

set(FIZMO_DIST_VERSION "0.9.0-alpha-1"
set(SUBPROJECT_INSTALL_PREFIX "${CMAKE_CURRENT_SOURCE_DIR}/install")

# "libfizmo" is always built since it's required for everything.
add_subdirectory(libfizmo)

#if(BUILD_SUBPROJECT_X)
#    add_subdirectory(some_dir)
#endif()

