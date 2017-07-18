cmake_minimum_required( VERSION 2.8.4 )
project( kaldi-lattice-search )
set( tool_EXE kaldi-lattice-search )

if( ${CMAKE_SOURCE_DIR} STREQUAL ${CMAKE_BINARY_DIR} )
  message( FATAL_ERROR "In-source builds not allowed." )
endif()

if( NOT DEFINED ENV{KALDI_ROOT} )
  message( FATAL_ERROR "KALDI_ROOT environment variable is undefined." )
endif()

add_custom_target( ${tool_EXE} ALL
  COMMAND make && mv ${tool_EXE} ${CMAKE_CURRENT_BINARY_DIR}
  WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} )

set_property( DIRECTORY APPEND PROPERTY ADDITIONAL_MAKE_CLEAN_FILES ${tool_EXE} )

install( PROGRAMS ${CMAKE_CURRENT_BINARY_DIR}/${tool_EXE} DESTINATION bin )
