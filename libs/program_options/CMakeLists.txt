cmake_minimum_required (VERSION 2.6)

file( GLOB Program_Option_Sources src/*.cpp )

include_directories( ../../ )

add_library(  bmp_program_options_lib ${Program_Option_Sources} )

set( MY_BOOST_LIBS ${MY_BOOST_LIBS} bmp_program_options_lib PARENT_SCOPE )

install(TARGETS 
 bmp_program_options_lib LIBRARY DESTINATION "lib"
  ARCHIVE DESTINATION "lib")

#set_property(TARGET BOOST_PROGRAM_OPTIONS_LIB APPEND PROPERTY COMPILE_FLAGS ${MY_BOOST_COMPILE_FLAGS} )	

