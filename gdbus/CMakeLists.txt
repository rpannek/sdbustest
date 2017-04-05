set(TARGET_NAME gdbusclient)

pkg_check_modules (DBUS       REQUIRED   dbus-1>=1.2.12)
pkg_check_modules (DBUS-GLIB  REQUIRED   dbus-glib-1>=0.80)

set(SRC_DIR ${CMAKE_CURRENT_SOURCE_DIR}/src)

include_directories(
    ${SRC_DIR}
    ${DBUS_INCLUDE_DIRS}
    ${DBUS-GLIB_INCLUDE_DIRS}
)
 
add_executable(${TARGET_NAME}
    ${SRC_DIR}/busclient.cpp
)

target_link_libraries(${TARGET_NAME}
    ${DBUS_LIBRARIES}
    ${DBUS-GLIB_LIBRARIES}
)
 
install(TARGETS ${TARGET_NAME} DESTINATION ${CMAKE_INSTALL_BINDIR})
