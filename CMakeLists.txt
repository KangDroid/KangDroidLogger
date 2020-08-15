cmake_minimum_required(VERSION 3.15)
project(KangDroidLogger)
set(CMAKE_MACOSX_RPATH 1)
add_library(KangDroidLogger SHARED Logger.cpp)

install(TARGETS KangDroidLogger
        DESTINATION ${CMAKE_INSTALL_PREFIX}/lib)
install(FILES Logger.h
        DESTINATION ${CMAKE_INSTALL_PREFIX}/include)
install(FILES cmake/KangDroidLoggerConfig.cmake
        DESTINATION ${CMAKE_INSTALL_PREFIX}/lib/cmake/KangDroidLogger/)