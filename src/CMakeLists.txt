FIND_PACKAGE(ZLIB REQUIRED)

SET(VERSION_MAJOR 0)
SET(VERSION_MINOR 0)
SET(VERSION_PATCH 0)

INCLUDE_DIRECTORIES(
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${MPL_INCLUDE_DIRS}
    ${GNOMEMENU_INCLUDE_DIRS}
    )


ADD_DEFINITIONS(-DLOCALEDIR="${LOCALEDIR}")
ADD_DEFINITIONS(-DMX_CACHE="${DATADIR}/mx.cache")
ADD_DEFINITIONS(-DTHEMEDIR="${PKG_DATADIR}/gogoo-panel-applications/theme")
ADD_DEFINITIONS(-DGETTEXT_PACKAGE="${GETTEXT_PACKAGE}")
ADD_DEFINITIONS(-DDATADIR="${PKG_DATADIR}")

SET (PROGRAMS gogoo-panel-applications)

SET(PROGRAM_SRCS
  mnb-entry.c
  mnb-entry.h
  mnb-expander.c
  mnb-expander.h
  mnb-filter.c
  mnb-filter.h
  mnb-launcher-application.c
  mnb-launcher-application.h
  mnb-launcher-button.c
  mnb-launcher-button.h
  mnb-launcher-grid.c
  mnb-launcher-grid.h
  mnb-launcher-tree.c
  mnb-launcher-tree.h
  meego-netbook-launcher.c
  meego-netbook-launcher.h
  meego-panel-applications.c
    )

SET(PROGRAM_HEADERS
    )

ADD_EXECUTABLE(${PROGRAMS} ${PROGRAM_SRCS} ${PROGRAM_HEADERS})

   
TARGET_LINK_LIBRARIES(${PROGRAMS}
    ${GNOMEMENU_LIBRARIES}
    ${MPL_LIBRARIES}
    )

INSTALL(TARGETS ${PROGRAMS} RUNTIME DESTINATION ${PKG_LIBEXECDIR})

########### Add .desktop target ###############
#CONFIGURE_FILE(
#  "${CMAKE_CURRENT_SOURCE_DIR}/meego-panel-internet.desktop.in"
#  "${CMAKE_CURRENT_BINARY_DIR}/meego-panel-internet.desktop"
#  IMMEDIATE @ONLY)
#INSTALL(FILES ${CMAKE_CURRENT_BINARY_DIR}/meego-panel-internet.desktop DESTINATION share/mutter-netbook/panels)

########### Add .service target ###############
CONFIGURE_FILE(
  "${CMAKE_CURRENT_SOURCE_DIR}/com.meego.UX.Shell.Panels.applications.service.in"
  "${CMAKE_CURRENT_BINARY_DIR}/com.meego.UX.Shell.Panels.applications.service"
  IMMEDIATE @ONLY)
INSTALL(FILES ${CMAKE_CURRENT_BINARY_DIR}/com.meego.UX.Shell.Panels.applications.service DESTINATION share/dbus-1/services)


