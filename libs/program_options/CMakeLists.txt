cmake_minimum_required (VERSION 2.6)



file( GLOB Program_Option_Sources src/*.cpp )

include_directories( ../../ )

add_library(  BOOST_PROGRAM_OPTIONS_LIB ${Program_Option_Sources} )

set( MY_BOOST_LIBS ${MY_BOOST_LIBS} BOOST_PROGRAM_OPTIONS_LIB PARENT_SCOPE )
