 #----------------------------------------------------------------------------
# USER! : SET THE NAME OF YOUR LIBRARY
# (Replace 'MyLib' by your own library name)

#############################
SET ( LIBRARY_NAME   ITKPCA  )
#############################

#----------------------------------------------------------------------------

#----------------------------------------------------------------------------
# CREATES A USER OPTION IN CMAKE
OPTION ( BUILD_${LIBRARY_NAME}  "Build ${LIBRARY_NAME} library ?" ON)
#----------------------------------------------------------------------------

#----------------------------------------------------------------------------
IF ( BUILD_${LIBRARY_NAME} )
#----------------------------------------------------------------------------

  #----------------------------------------------------------------------------
  # BUILD LIBRARY
  #----------------------------------------------------------------------------

  #----------------------------------------------------------------------------
  # LIBRARY HEADERS (TO BE INSTALLED)
  # EITHER LIST ALL .h, *.txx IN CURRENT DIR USING NEXT LINE:

  FILE(GLOB ${LIBRARY_NAME}_HEADERS "*.h" "*.cpp")
  
  # OR MANUALLY LIST YOUR HEADERS WITH NEXT COMMAND
  #  SET ( ${LIBRARY_NAME}_HEADERS
  #
  #      )
  #----------------------------------------------------------------------------

  #----------------------------------------------------------------------------
  # LIBRARY SOURCES (TO BE COMPILED)
  # EITHER LIST ALL .cxx, *.cpp, *.cc IN CURRENT DIR USING NEXT LINE:

  FILE(GLOB ${LIBRARY_NAME}_SOURCES *.cxx *.cc ${${LIBRARY_NAME}_HEADERS})

  # OR MANUALLY LIST YOUR FILES WITH NEXT COMMAND (WITHOUT EXTENSION)
  #  SET ( ${LIBRARY_NAME}_SOURCES 
  #   
  #      )
  #----------------------------------------------------------------------------

  #----------------------------------------------------------------------------
  # LIBRARY DEPENDENCIES (LIBRARIES TO LINK WITH)
  #
  # USER! : Uncomment the Libraries you need
  #
  SET ( ${LIBRARY_NAME}_LINK_LIBRARIES
  #    ${crea_LIBRARIES}
  #    ${WXWIDGETS_LIBRARIES}
  #    ${KWWidgets_LIBRARIES}
  #    ${VTK_LIBRARIES}
      ${ITK_LIBRARIES}
  #    ${GDCM_LIBRARIES}
  #    ${BOOST_LIBRARIES}

  # If this library must link against other libraries 
  # USER! : Add here any extra Library you need

      )
  #----------------------------------------------------------------------------

  #----------------------------------------------------------------------------
  # MACRO WHICH DOES ALL THE JOB : BUILD AND INSTALL

  # USER! : The default is to create a Dynamic Library.
  # if you need to create a static library
  # comment out the following line :

  SET(${LIBRARY_NAME}_INSTALL_TREE_RELATIVE_INCLUDE_PATHS include/creaANN)
  SET(${LIBRARY_NAME}_INSTALL_FOLDER creaANN)
  
  # and uncomment the 2 lines hereafter:

   #ADD_LIBRARY(${LIBRARY_NAME} STATIC  ${${LIBRARY_NAME}_SOURCES})
   #TARGET_LINK_LIBRARIES(${LIBRARY_NAME} ${${LIBRARY_NAME}_LINK_LIBRARIES} )
   #SET_TARGET_PROPERTIES(${LIBRARY_NAME} PROPERTIES LINKER_LANGUAGE C)

  #
  #----------------------------------------------------------------------------

  #---------------------------------------------------------------------------
ENDIF ( BUILD_${LIBRARY_NAME} )
