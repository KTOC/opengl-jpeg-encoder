cmake_minimum_required(VERSION 3.9)
project(ojenc VERSION 0.0.1 DESCRIPTION "OpenGL Jpeg Encoder")

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/CMake/")

SET(OpenGL_GL_PREFERENCE "GLVND")
find_package(OpenGL REQUIRED)
add_library(OpenGL SHARED IMPORTED)
add_library(EGL SHARED IMPORTED)

find_package(DRM REQUIRED)
add_library(DRM SHARED IMPORTED)

find_package(GBM REQUIRED)
add_library(GBM SHARED IMPORTED)

add_library(ojenc SHARED
        src/ojenc.c include/ojenc.h)
set_property(TARGET ojenc PROPERTY C_STANDARD 11)
set_target_properties(ojenc PROPERTIES SOVERSION 1)
set_target_properties(ojenc PROPERTIES PUBLIC_HEADER include/ojenc.h)
target_include_directories(ojenc PRIVATE include)
target_include_directories(ojenc PRIVATE src)
include(GNUInstallDirs)
install(TARGETS ojenc
        LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
        PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})
configure_file(ojenc.pc.in ojenc.pc @ONLY)
install(FILES ${CMAKE_BINARY_DIR}/ojenc.pc DESTINATION ${CMAKE_INSTALL_DATAROOTDIR}/pkgconfig)
