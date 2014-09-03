cmake_minimum_required (VERSION 2.6)



file( GLOB System_Sources src/*.cpp )

include_directories( ../../ )



add_library(  bmp_system_lib ${System_Sources} )


set( MY_BOOST_LIBS ${MY_BOOST_LIBS} bmp_system_lib PARENT_SCOPE )


install(TARGETS 
 bmp_system_lib LIBRARY DESTINATION "lib"
  ARCHIVE DESTINATION "lib")

#set_property(TARGET BOOST_SYSTEM_LIB APPEND PROPERTY COMPILE_FLAGS ${MY_BOOST_COMPILE_FLAGS} )	