ADD_SUBDIRECTORY(theme)

########### Add .desktop target ###############
CONFIGURE_FILE(
  "${CMAKE_CURRENT_SOURCE_DIR}/meego-panel-applications.desktop.in"
  "${CMAKE_CURRENT_BINARY_DIR}/meego-panel-applications.desktop"
  IMMEDIATE @ONLY)
INSTALL(FILES ${CMAKE_CURRENT_BINARY_DIR}/meego-panel-applications.desktop DESTINATION share/mutter-neetbook/panels)


