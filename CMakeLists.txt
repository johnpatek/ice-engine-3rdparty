cmake_minimum_required(VERSION 3.0)

project(ice-engine-3rdparty)

set(CMAKE_INSTALL_PREFIX ${PROJECT_SOURCE_DIR}/install)
if(WIN32)
add_subdirectory(zlib)
endif(WIN32)

set(LIBUV_INCLUDE_DIR ${PROJECT_SOURCE_DIR}/libuv/include)
link_directories(${PROJECT_BINARY_DIR}/libuv)
set(LIBUV_LIBRARY uv)

add_subdirectory(json11)
add_subdirectory(capnproto)
add_subdirectory(libuv)
add_subdirectory(uWebSocketsCMake)
add_subdirectory(cpprestsdk)