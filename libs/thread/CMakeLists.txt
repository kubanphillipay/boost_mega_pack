cmake_minimum_required (VERSION 2.6)



file( GLOB Thread_Sources src/*.cpp )

include_directories( ../../ )

if( WIN32 )
#	list(REMOVE_ITEM Thread_Sources "*/pthread/*")
	file( GLOB Win32_Thread_Sources src/win32/*.cpp )
	list( APPEND Thread_Sources ${Win32_Thread_Sources} )
else()
#	file( GLOB Unix_Thread_sources ${CMAKE_CURRENT_SOURCE_DIR}/src/pthread/*.cpp )
	file( GLOB Unix_Thread_Sources src/pthread/*.cpp )
	list( APPEND Thread_Sources ${Unix_Thread_Sources} )
#	message( "Adding Unix Sources" )

endif()


#foreach( THR_SRC ${Thread_Sources} )
#	message( STATUS "Thread source is : ${THR_SRC}" )
#endforeach( THR_SRC )

add_library(  BOOST_THREAD_LIB ${Thread_Sources} )

set( MY_BOOST_LIBS ${MY_BOOST_LIBS} BOOST_THREAD_LIB PARENT_SCOPE )
