cmake_minimum_required (VERSION 2.6)



file( GLOB System_Sources src/*.cpp )

include_directories( ../../ )

set( MY_BOOST_LIBS ${MY_BOOST_LIBS} BOOST_SYSTEM_LIB PARENT_SCOPE )

add_library(  BOOST_SYSTEM_LIB ${System_Sources} )