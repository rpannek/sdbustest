set(TARGET_NAME sdbusclient)

find_package(PkgConfig REQUIRED)
pkg_check_modules(LIBSYSTEMD REQUIRED libsystemd)
  
set(SRC_DIR ${CMAKE_CURRENT_SOURCE_DIR}/src)

include_directories(
    ${SRC_DIR}
    ${LIBSYSTEMD_INCLUDE_DIRS}
)
 
add_executable(${TARGET_NAME}
    ${SRC_DIR}/busclient.cpp
)

target_link_libraries(${TARGET_NAME} ${LIBSYSTEMD_LDFLAGS})
 
install(TARGETS ${TARGET_NAME} DESTINATION ${CMAKE_INSTALL_BINDIR})
