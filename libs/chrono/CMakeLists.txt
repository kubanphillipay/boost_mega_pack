cmake_minimum_required (VERSION 2.6)


file( GLOB Chrono_Sources src/*.cpp )

include_directories( ../../ )

add_library(  bmp_chrono_lib ${Chrono_Sources} )

set( MY_BOOST_LIBS ${MY_BOOST_LIBS} bmp_chrono_lib PARENT_SCOPE )

install(TARGETS 
bmp_chrono_lib LIBRARY DESTINATION "lib"
  ARCHIVE DESTINATION "lib")

#set_property(TARGET BOOST_CHRONO_LIB APPEND PROPERTY COMPILE_FLAGS ${MY_BOOST_COMPILE_FLAGS} )	
#set_property(TARGET BOOST_CHRONO_LIB APPEND PROPERTY COMPILE_DEFINITIONS ${MY_BOOST_DEFINITIONS} )

