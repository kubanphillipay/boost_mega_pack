cmake_minimum_required (VERSION 2.6)

file( GLOB FileSystem_Sources src/*.cpp )

include_directories( ../../ )

add_library( bmp_filesystem_lib ${FileSystem_Sources} )

set( MY_BOOST_LIBS ${MY_BOOST_LIBS} bmp_filesystem_lib PARENT_SCOPE )

install(TARGETS 
 bmp_filesystem_lib LIBRARY DESTINATION "lib"
  ARCHIVE DESTINATION "lib")

#set_property(TARGET BOOST_PROGRAM_OPTIONS_LIB APPEND PROPERTY COMPILE_FLAGS ${MY_BOOST_COMPILE_FLAGS} )	

