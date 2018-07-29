cmake_minimum_required(VERSION 3.9)
project(ojenc VERSION 0.0.1 DESCRIPTION "OpenGL Jpeg Encoder")
add_library(ojenc SHARED
        src/ojenc.c include/ojenc.h)
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
