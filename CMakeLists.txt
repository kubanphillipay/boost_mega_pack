cmake_minimum_required (VERSION 2.6)


#
#Boost mega pack
#
#
#
#
#

project (BOOST_MEGA_PACK)

#message( STATUS "In Boost Libraries.test.." )

########### Set cache variables ############


set( BMP_USE_STATIC_RUNTIME OFF CACHE BOOL "Use Static runtime" )
set( BMP_USE_STATIC_LIBS ON CACHE BOOL "Build static libraries" )

set( BMP_SYSTEM ON CACHE BOOL "Use System Library" )
set( BMP_PROGRAM_OPTIONS ON CACHE BOOL "Use Program Options" )
set( BMP_FILESYSTEM ON CACHE BOOL "Use FileSystem" )
set( BMP_CHRONO ON CACHE BOOL "Use Chrono" )
set( BMP_THREAD ON CACHE BOOL "Use Thread" )

set( MY_BOOST_PACKAGES )

if( BMP_SYSTEM )
	set( MY_BOOST_PACKAGES ${MY_BOOST_PACKAGES} "system" )
endif()

if( BMP_PROGRAM_OPTIONS )
	set( MY_BOOST_PACKAGES ${MY_BOOST_PACKAGES} "program_options" )
endif()

if( BMP_FILESYSTEM )
	set( MY_BOOST_PACKAGES ${MY_BOOST_PACKAGES} "filesystem" )
endif()

if( BMP_CHRONO )
	set( MY_BOOST_PACKAGES ${MY_BOOST_PACKAGES} "chrono" )
endif()

if( BMP_THREAD )
	set( MY_BOOST_PACKAGES ${MY_BOOST_PACKAGES} "thread" )
endif()




########## set variables ################


set( Boost_USE_STATIC_RUNTIME  ${BMP_USE_STATIC_RUNTIME} )
set( Boost_USE_STATIC_LIBS  ${BMP_USE_STATIC_LIBS} )




############ Check whether to use static runtime ###########
if( Boost_USE_STATIC_RUNTIME )
	if( WIN32 )
		message( STATUS "Using boost static runtime" )
		if( MY_BOOST_DEBUG )
			set( MY_BOOST_COMPILE_FLAGS "/MTd" )
		else()
			set( MY_BOOST_COMPILE_FLAGS "/MT" )
		endif()
	else()
		message( FATAL_ERROR "BOOST STATIC RUNTIME ONLY SETUP FOR WINDOWS RIGHT NOW" )
	endif()
endif()


############ Check whether to build static libraries ###########
if( NOT Boost_USE_STATIC_LIBS )
	message( FATAL_ERROR "Boost not setup for shared libraries yet..." )
else()
	message( STATUS "Boost using static libraries" )
endif()


############ disable auto linking on windows ###########
if( WIN32 )
	#set( MY_BOOST_DEFINITIONS "BOOST_ALL_NO_LIB" PARENT_SCOPE )
	add_definitions( -DBOOST_ALL_NO_LIB )
endif()


########### Set include dir ##############
set( MY_BOOST_INCLUDE_DIR ${PROJECT_SOURCE_DIR} )


##################### Find sub packages ################
#set( MY_BOOST_LIBS )
foreach( BOOST_LIB ${MY_BOOST_PACKAGES} )
	message( STATUS "Looking for boost lib: ${BOOST_LIB}" )

	if( ${BOOST_LIB} STREQUAL "system" )
		#message( STATUS "adding boost system lib" )
		add_subdirectory( libs/system )
	elseif( ${BOOST_LIB} STREQUAL "program_options" )
		#message( STATUS "adding boost program_options lib" )
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
	elseif( ${BOOST_LIB} STREQUAL "smart_ptr" )
		#message( STATUS adding boost smart_ptr lib )
		add_subdirectory( libs/smart_ptr )
	else()
		message( FATAL_ERROR "Looking for boost library that does not exist "
				     "or does not have a cmake file written yet: " 
				     "${BOOST_LIB}")
	endif()
endforeach( BOOST_LIB )




####### #FOR DEBUGGING #####################
foreach( FOUND_LIBS ${MY_BOOST_LIBS} )
	message( STATUS "Found This LIb: ${FOUND_LIBS}" )
endforeach( FOUND_LIBS )
#
#message( STATUS "MY boost libs: ${MY_BOOST_LIBS}" )
#message( STATUS "MY boost include dir: ${MY_BOOST_INCLUDE_DIR}" )



######## END DEBUGGING #############
#set this up for parent scope
#set( MY_BOOST_LIBS ${MY_BOOST_LIBS} PARENT_SCOPE )
#set( MY_BOOST_INCLUDE_DIR ${MY_BOOST_INCLUDE_DIR} PARENT_SCOPE )
#set( MY_BOOST_DEFINITIONS ${MY_BOOST_DEFINITIONS} PARENT_SCOPE )


##### NEED TO INSTALL #############


install(FILES boost_mega_pack.h DESTINATION include/boost)
install( DIRECTORY boost/ DESTINATION include/boost/boost FILES_MATCHING PATTERN "*hpp" PATTERN "*ipp"  )



