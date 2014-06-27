cmake_minimum_required (VERSION 2.6)



file( GLOB Chrono_Sources src/*.cpp )

include_directories( ../../ )

add_library(  BOOST_CHRONO_LIB ${Chrono_Sources} )

set( MY_BOOST_LIBS ${MY_BOOST_LIBS} BOOST_CHRONO_LIB PARENT_SCOPE )
