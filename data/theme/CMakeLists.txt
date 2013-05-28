SET(THEME_SRCS
	toolbar-button.css
	apps-coloured.png 
	apps-normal.png
	panel.css
	clear-entry.png
	content-pane-background.png
	content-pane-header.png
	launcher-button-fav-toggle-active.png
	launcher-button-fav-toggle-checked.png
	launcher-button-fav-toggle-hover.png
	launcher-button-fav-toggle.png
	launcher-hover.png
	launcher-search-bg.png
    )

INSTALL(FILES ${THEME_SRCS} DESTINATION ${PKG_DATADIR}/${PROGRAMS}/theme)



