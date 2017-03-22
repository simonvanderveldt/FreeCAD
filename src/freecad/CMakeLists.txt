
INSTALL(FILES "__init__.py" DESTINATION "Mod/freecad/")

if(BUILD_ARCH)
  add_subdirectory(Arch)
endif(BUILD_ARCH)
