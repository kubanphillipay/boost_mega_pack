cmake_minimum_required (VERSION 2.6)


#
#Boost mega pack
#
#
#
#
#

project (Boost_Libaries)

message( STATUS "In Boost Libraries..." )

set( MY_BOOST_INCLUDE_DIR ${PROJECT_SOURCE_DIR} )

set( MY_BOOST_LIBS )

foreach( BOOST_LIB ${MY_BOOST_PACKAGES} )
#	message( STATUS "Looking for boost lib: ${BOOST_LIB}" )

	if( ${BOOST_LIB} STREQUAL "system" )
		#message( STATUS "adding boost system lib" )
		add_subdirectory( libs/system )
	elseif( ${BOOST_LIB} STREQUAL "program_options" )
		#message( STATUS "adding boost program options lib" )
		add_subdirectory( libs/program_options )
	elseif( ${BOOST_LIB} STREQUAL "filesystem" )
		#message( STATUS adding boost filesystem lib )
		add_subdirectory( libs/filesystem )
	elseif( ${BOOST_LIB} STREQUAL "chrono" )
		#message( STATUS adding boost chrono lib )
		add_subdirectory( libs/chrono )
	elseif( ${BOOST_LIB} STREQUAL "thread" )
		#message( STATUS adding boost thread lib )
		add_subdirectory( libs/thread )
	else()
		message( FATAL_ERROR "Looking for boost library that does not exist "
				     "or does not have a cmake file written yet: " 
				     "${BOOST_LIB}")
	endif()
endforeach( BOOST_LIB )






####### #FOR DEBUGGING #####
#foreach( FOUND_LIBS ${MY_BOOST_LIBS} )
#	message( STATUS "Found This LIb: ${FOUND_LIBS}" )
#endforeach( FOUND_LIBS )

message( STATUS "MY boost libs: ${MY_BOOST_LIBS}" )
#message( STATUS "MY boost include dir: ${MY_BOOST_INCLUDE_DIR}" )

######## END DEBUGGING #############


#set this up for parent scope
set( MY_BOOST_LIBS ${MY_BOOST_LIBS} PARENT_SCOPE )
set( MY_BOOST_INCLUDE_DIR ${MY_BOOST_INCLUDE_DIR} PARENT_SCOPE )
if( WIN32 )
	set( MY_BOOST_DEFINITIONS "BOOST_ALL_NO_LIB" PARENT_SCOPE )
endif()



##################################

############### Here be dragons

###########################3
#add_subdirectory( boost_libraries )

#message( STATUS "Boost Include Dir: ${BOOST_INCLUDE_DIR}" )
#message( STATUS "Boost Definitions: ${BOOST_DEFINITIONS}" )


#set( ALL_LIBS ${BOOST_LIBS} )

#foreach( BLIB ${BOOST_LIBS} )
#   message( STATUS "Boost Lib ${BLIB} found" )
#endforeach(BLIB)


#include_directories(
#        ${PROJECT_BINARY_DIR}
#	${BOOST_INCLUDE_DIR}
#)


#add_subdirectory( myexe )

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
