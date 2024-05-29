
#[[

  CMakeLists.txt

  This file is part of fizmo.

  ---

  Copyright (c) 2010-2024 Christoph Ender.
  All rights reserved.

  Redistribution and use in source and binary forms, with or without
  modification, are permitted provided that the following conditions
  are met:
  1. Redistributions of source code must retain the above copyright
  notice, this list of conditions and the following disclaimer.
  2. Redistributions in binary form must reproduce the above copyright
  notice, this list of conditions and the following disclaimer in the
  documentation and/or other materials provided with the distribution.
  3. Neither the name of the copyright holder nor the names of its
  contributors may be used to endorse or promote products derived
  from this software without specific prior written permission.

  THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS
  IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO,
  THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR
  PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR
  CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL,
  EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
  PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR
  PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF
  LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING
  NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
  SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

  ---



  This is the main buildfile for fizmo. It will build all the required
  libraries for the frontends which are selected via CMake-options.

]]


cmake_minimum_required(VERSION 3.10)

project(fizmo
  LANGUAGES C
  DESCRIPTION "fizmo z-machine interpreter"
  VERSION 0.9.0)

option(BUILD_FIZMO_CONSOLE "Enable building fizmo-console" ON)

# The following two interval variables are set by the configuration
# prozess of libfizmo and will contain the libraries and requirements
# which are needed for other components to link to libfizmo.
# LIBFIZMO_LIBRARIES typically contains the two elements "libfizmo"
# and "m", whereas LIBFIZMO_REQUIRES may for example contain
# "libxml-2.0". Libraries are directly linked, requirements instead
# are resolved using "pkg_check_modules" instead.
set(LIBFIZMO_LIBRARIES "" CACHE INTERNAL "")
set(LIBFIZMO_REQUIRES "" CACHE INTERNAL "")

#set(SUBPROJECT_INSTALL_PREFIX "${CMAKE_CURRENT_SOURCE_DIR}/install" CACHE STRING "project")

#set(FIZMO_DIST_VERSION "0.9.0")
#set(SUBPROJECT_INSTALL_PREFIX "${CMAKE_CURRENT_SOURCE_DIR}/install")

# Add the "install" directory to CMake's pkg_config search:
#set(CMAKE_PREFIX_PATH "${CMAKE_CURRENT_SOURCE_DIR}/install")

# "libfizmo" is always built since it's required for everything.
add_subdirectory(libfizmo)

if(BUILD_FIZMO_CONSOLE)
    add_subdirectory(fizmo-console)
endif()

