cmake_minimum_required (VERSION 2.6)



file( GLOB Thread_Sources src/future.cpp )

include_directories( ../../ )

if( WIN32 )
	list(REMOVE_ITEM Thread_Sources "tss_null.cpp")
	list( APPEND Thread_Sources 
		src/win32/thread.cpp 
		src/win32/tss_pe.cpp
	)
else()
#	file( GLOB Unix_Thread_sources ${CMAKE_CURRENT_SOURCE_DIR}/src/pthread/*.cpp )
	file( GLOB Unix_Thread_Sources src/pthread/*.cpp )
	list( APPEND Thread_Sources ${Unix_Thread_Sources} )
#	message( "Adding Unix Sources" )

endif()


#foreach( THR_SRC ${Thread_Sources} )
#	message( STATUS "Thread source is : ${THR_SRC}" )
#endforeach( THR_SRC )

if( Boost_USE_STATIC_LIBS )
	add_definitions( -DBOOST_THREAD_BUILD_LIB )
else()
	message( STATUS "Threads not setup to build dll" )
endif()

add_library(  bmp_thread_lib ${Thread_Sources} )

set( MY_BOOST_LIBS ${MY_BOOST_LIBS} bmp_thread_lib PARENT_SCOPE )

install(TARGETS 
 bmp_thread_lib LIBRARY DESTINATION "lib"
  ARCHIVE DESTINATION "lib")


#######################
