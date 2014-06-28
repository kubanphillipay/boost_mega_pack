cmake_minimum_required (VERSION 2.6)



file( GLOB System_Sources src/*.cpp )

include_directories( ../../ )

set( MY_BOOST_LIBS ${MY_BOOST_LIBS} BOOST_SYSTEM_LIB PARENT_SCOPE )

add_library(  BOOST_SYSTEM_LIB ${System_Sources} )

set_property(TARGET BOOST_SYSTEM_LIB APPEND PROPERTY COMPILE_FLAGS ${MY_BOOST_COMPILE_FLAGS} )	