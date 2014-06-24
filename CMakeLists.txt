cmake_minimum_required (VERSION 2.6)


project (FileDemoBoost)



add_subdirectory( boost_libraries )

#message( STATUS "Boost Include Dir: ${BOOST_INCLUDE_DIR}" )
#message( STATUS "Boost Definitions: ${BOOST_DEFINITIONS}" )


set( ALL_LIBS ${BOOST_LIBS} )

#foreach( BLIB ${BOOST_LIBS} )
#   message( STATUS "Boost Lib ${BLIB} found" )
#endforeach(BLIB)


#include_directories(
#        ${PROJECT_BINARY_DIR}
#	${BOOST_INCLUDE_DIR}
#)


add_subdirectory( myexe )

#set ( VERSION_MAJOR 1 )
#set ( VERSION_MINOR 0 )
#set ( MEDIA_DIRECTORY "${PROJECT_SOURCE_DIR}/media" )

#configure_file (
#  "${PROJECT_SOURCE_DIR}/include.h.in"
#  "${PROJECT_BINARY_DIR}/include.h"
#)


#set( HEADERS myclass.h )

#set( SOURCES tut4.cpp )













#message (STATUS ":Done" )

#add_executable( FileDemo ${SOURCES} ${HEADERS} )

#set_property(TARGET FileDemo APPEND PROPERTY COMPILE_DEFINITIONS ${BOOST_DEFINITIONS} )

#target_link_libraries( FileDemo ${ALL_LIBS}  )