cmake_minimum_required (VERSION 2.6)



file( GLOB System_Sources src/*.cpp )

include_directories( ../../ )

#message( STATUS "System BOOST DEF: ${BOOST_DEFINITIONS}" )

add_library(  BOOST_SYSTEM_LIB ${Program_Option_Sources} )

set_property(TARGET BOOST_SYSTEM_LIB APPEND PROPERTY COMPILE_DEFINITIONS ${MY_BOOST_DEFINITIONS} )

set( MY_BOOST_LIBS ${MY_BOOST_LIBS} BOOST_SYSTEM_LIB )