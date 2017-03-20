include_directories(
    ${CMAKE_CURRENT_BINARY_DIR}
    ${Boost_INCLUDE_DIRS}
    ${COIN3D_INCLUDE_DIRS}
    ${ZLIB_INCLUDE_DIR}
    ${PYTHON_INCLUDE_DIRS}
    ${XercesC_INCLUDE_DIRS}
)

set(StartGui_LIBS
    FreeCADGui
)

if(BUILD_QT5)
    qt5_add_resources(Start_QRC_SRCS Resources/Start.qrc)
else()
    qt4_add_resources(Start_QRC_SRCS Resources/Start.qrc)
endif()

SET(StartGui_SRCS
    ${Start_QRC_SRCS}
    AppStartGui.cpp
    Command.cpp
    PreCompiled.cpp
    PreCompiled.h
    Workbench.cpp
    Workbench.h
)

add_library(StartGui SHARED ${StartGui_SRCS})
target_link_libraries(StartGui ${StartGui_LIBS})

SET_BIN_DIR(StartGui StartGui /Mod/Start)
SET_PYTHON_PREFIX_SUFFIX(StartGui)

INSTALL(TARGETS StartGui DESTINATION Mod/freecad/Start)

SET(StartGuiIcon_SVG
    Resources/icons/StartWorkbench.svg
)

fc_copy_sources(StartGui "${CMAKE_BINARY_DIR}/${CMAKE_INSTALL_DATADIR}/freecad/Start" ${StartGuiIcon_SVG})

INSTALL(FILES ${StartGuiIcon_SVG} DESTINATION "Mod/freecad/Start/Gui/Resources/icons")
