cmake_minimum_required(VERSION 2.8)
project(busclient)
  
set(PROJECT_MAJOR_VERSION 0)
set(PROJECT_MINOR_VERSION 1)
set(PROJECT_PATCH_LEVEL 0)
set(PROJECT_VERSION ${PROJECT_MAJOR_VERSION}.${PROJECT_MINOR_VERSION}.${PROJECT_PATCH_LEVEL})
 
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -std=c++11")
# Sets various paths used in e.g. pc.in files
# as well as install target paths
include(GNUInstallDirs)

find_package(PkgConfig REQUIRED)
pkg_check_modules(LIBSYSTEMD REQUIRED libsystemd)
  
set(SRC_DIR ${CMAKE_CURRENT_SOURCE_DIR}/src)

include_directories(
    ${SRC_DIR}
    ${LIBSYSTEMD_INCLUDE_DIRS}
)
 
add_executable(${PROJECT_NAME}
    ${SRC_DIR}/busclient.cpp
)

target_link_libraries(${PROJECT_NAME} ${LIBSYSTEMD_LDFLAGS})
 
install(TARGETS ${TARGET_NAME} DESTINATION ${CMAKE_INSTALL_BINDIR})
