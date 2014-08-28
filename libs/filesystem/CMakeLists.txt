cmake_minimum_required (VERSION 2.6)

file( GLOB FileSystem_Sources src/*.cpp )

include_directories( ../../ )

add_library(  BOOST_FILESYSTEM_LIB ${FileSystem_Sources} )

set( MY_BOOST_LIBS ${MY_BOOST_LIBS} BOOST_FILESYSTEM_LIB PARENT_SCOPE )

install(TARGETS 
 BOOST_FILESYSTEM_LIB LIBRARY DESTINATION "lib"
  ARCHIVE DESTINATION "lib")

#set_property(TARGET BOOST_PROGRAM_OPTIONS_LIB APPEND PROPERTY COMPILE_FLAGS ${MY_BOOST_COMPILE_FLAGS} )	

