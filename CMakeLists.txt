cmake_minimum_required(VERSION 3.0)

project(ice-engine-3rdparty)

set(CMAKE_INSTALL_PREFIX ${PROJECT_SOURCE_DIR}/install)

add_subdirectory(cpprestsdk)
add_subdirectory(googletest)