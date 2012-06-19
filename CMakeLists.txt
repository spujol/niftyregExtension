cmake_minimum_required(VERSION 2.8.7)

#-----------------------------------------------------------------------------
SET(MODULE_NAME niftyregExtension) # Do not use 'project()'

#-----------------------------------------------------------------------------
SET(MODULE_HOMEPAGE "http://www.slicer.org/slicerWiki/index.php/Documentation/Snapshot/Developers/Tutorials/ExtensionWriting")
SET(MODULE_CATEGORY "Examples")
SET(MODULE_STATUS "Beta")
SET(MODULE_CONTRIBUTORS "Pr. Sonia Pujol and her assistant Marc Modat")
SET(MODULE_DESCRIPTION "This is an example of CLI module built as an extension")
SET(MODULE_ICONURL "http://viewvc.slicer.org/viewvc.cgi/Slicer4/trunk/Extensions/Testing/niftyregExtension/niftyregExtension.png?revision=19437&view=co")
SET(MODULE_SCREENSHOTURLS "http://wiki.slicer.org/slicerWiki/images/a/ab/Slicer-r19441-niftyregExtension-screenshot.png http://wiki.slicer.org/slicerWiki/images/1/1e/Slicer-r19441-niftyregExtension-screenshot-2.png")
SET(MODULE_ACKNOWLEDGEMENTS "This work was supported by ...")
SET(MODULE_MAJOR_VERSION 0)
SET(MODULE_MINOR_VERSION 1)
SET(MODULE_PATCH_VERSION 0)

#-----------------------------------------------------------------------------
IF(NOT Slicer_SOURCE_DIR)
  FIND_PACKAGE(Slicer REQUIRED)
  INCLUDE(${Slicer_USE_FILE})
ENDIF()

# Configure XML description
CONFIGURE_FILE(
  ${MODULE_NAME}.xml.in
  ${CMAKE_CURRENT_BINARY_DIR}/${MODULE_NAME}.xml
  @ONLY
  )

#-----------------------------------------------------------------------------
#add_subdirectory(Logic)

#-----------------------------------------------------------------------------
SET(MODULE_INCLUDE_DIRECTORIES
  )

SET(MODULE_SRCS
  )

SET(MODULE_TARGET_LIBRARIES
  ${ITK_LIBRARIES}
  )

#-----------------------------------------------------------------------------
SEMMacroBuildCLI(
  NAME ${MODULE_NAME}
  #LOGO_HEADER ${Slicer_SOURCE_DIR}/Resources/NAMICLogo.h
  TARGET_LIBRARIES ${MODULE_TARGET_LIBRARIES}
  INCLUDE_DIRECTORIES ${MODULE_INCLUDE_DIRECTORIES}
  ADDITIONAL_SRCS ${MODULE_SRCS}
  #EXECUTABLE_ONLY
  )

#-----------------------------------------------------------------------------
IF(BUILD_TESTING)
  ADD_SUBDIRECTORY(Testing)
ENDIF()

#-----------------------------------------------------------------------------
if(NOT Slicer_SOURCE_DIR)
  INCLUDE(${Slicer_EXTENSION_CPACK})
endif()
