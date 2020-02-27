cmake_minimum_required(VERSION 3.0)

project(ice-engine-3rdparty)

set(CMAKE_INSTALL_PREFIX ${PROJECT_SOURCE_DIR}/install)

set(LIBUV_INCLUDE_DIR ${PROJECT_SOURCE_DIR}/libuv/include)
link_directories(${PROJECT_BINARY_DIR}/libuv)
set(LIBUV_LIBRARY uv)

add_subdirectory(libuv)
add_subdirectory(uWebSocketsCMake)
add_subdirectory(googletest)
add_subdirectory(sdl2)

set(VERSION_MAJOR 0)
set(VERSION_MINOR 0)
set(VERSION_PATCH 0)

if (WIN32)
    set(PLATFORM "WINDOWS")
    set(PACKAGE "MSI")
elseif (APPLE)
    set(PACKAGE "APPLE")
    set(PLATFORM "APPLE")
    set(GENERATOR "APPLE")
else()
    set(PACKAGE "DEB")
    set(PLATFORM "UBUNTU")
    set(GENERATOR "DEBIAN")
endif()

set(CPACK_GENERATOR ${PACKAGE})

if(WIN32)
    set(CPACK_PACKAGING_INSTALL_PREFIX "C:/Program Files/ice-common")
else()
    set(CPACK_PACKAGING_INSTALL_PREFIX /usr/share/ice-common)
endif()

set(CPACK_PACKAGE_CONTACT "John R. Patek <johnpatek2@gmail.com>")
set(CPACK_PACKAGE_DESCRIPTION "ICEngine Dependencies")
set(CPACK_PACKAGE_VERSION_MAJOR ${VERSION_MAJOR})
set(CPACK_PACKAGE_VERSION_MINOR ${VERSION_MINOR})
set(CPACK_PACKAGE_VERSION_PATCH ${VERSION_PATCH})
set(CPACK_PACKAGE_VENDOR "John Patek")
set(CPACK_PACKAGE_FILE_NAME "${CMAKE_PROJECT_NAME}-${VERSION_MAJOR}.${VERSION_MINOR}.${VERSION_PATCH}")
include (CPack)