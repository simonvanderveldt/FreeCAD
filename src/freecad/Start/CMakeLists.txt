
add_subdirectory(App)

if(BUILD_GUI)
    add_subdirectory(Gui)
    INSTALL(DIRECTORY StartPage
        DESTINATION Mod/freecad/Start
    )
endif(BUILD_GUI)

INSTALL(
    FILES
        __init__.py
        InitGui.py
    DESTINATION
        Mod/freecad/Start
)
