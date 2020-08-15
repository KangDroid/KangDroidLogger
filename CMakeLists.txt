cmake_minimum_required(VERSION 3.15)
project(KangDroidLogger)
set(CMAKE_MACOSX_RPATH 1)
add_library(KangDroidLogger STATIC Logger.cpp)

set(CMAKE_INSTALL_PREFIX "/Users/kangdroid/Desktop/test")
set(CMAKE_BUILD_TYPE "Release")

# export(TARGETS
#         KangDroidLogger
#     NAMESPACE YourPackage::
#     FILE "${CMAKE_CURRENT_BINARY_DIR}/YourPackageConfig.cmake"
# )

install(TARGETS KangDroidLogger
        DESTINATION ${CMAKE_INSTALL_PREFIX}/lib)
install(FILES Logger.h
        DESTINATION ${CMAKE_INSTALL_PREFIX}/include)
install(FILES cmake/KangDroidLoggerConfig.cmake
        DESTINATION ${CMAKE_INSTALL_PREFIX}/lib/cmake/KangDroidLogger/)