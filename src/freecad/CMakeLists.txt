
INSTALL(FILES "__init__.py" DESTINATION "Mod/freecad/")

if(BUILD_ARCH)
  add_subdirectory(Arch)
endif(BUILD_ARCH)

if(BUILD_START)
  add_subdirectory(Start)
endif(BUILD_START)

if(BUILD_WEB)
  add_subdirectory(Web)
endif(BUILD_WEB)
