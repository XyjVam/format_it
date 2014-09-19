CMAKE_MINIMUM_REQUIRED(VERSION 2.6)
PROJECT(format_it)

SET( CMAKE_BUILD_TYPE RELEASE )

#SET( CMAKE_C_COMPILER clang++ )
#SET( CMAKE_CXX_COMPILER clang++ )
SET( CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -march=native -DDISABLE_GTEST" )
SET( CMAKE_C_FLAGS_DEBUG "${CMAKE_C_FLAGS_DEBUG} -Wall -pedantic -DGLIBCXX_DEBUG -fsanitize=address" )
SET( CMAKE_CXX_FLAGS "${CMAKE_C_FLAGS} ${CMAKE_CXX_FLAGS} -std=c++1y" )
SET( CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} ${CMAKE_C_FLAGS_DEBUG}" )
SET( CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE}" )

SET( CMAKE_EXPORT_COMPILE_COMMANDS on )

ADD_SUBDIRECTORY ( double_conversion EXCLUDE_FROM_ALL )
ADD_EXECUTABLE(bin_format_it main.cpp)
ADD_LIBRARY(format_it 
  format_float.cpp
  format_helpers.cpp
  format_integers.cpp
  format_it.cpp
  format_out.cpp
  format_stl.cpp
  stack_format.cpp
  )

TARGET_LINK_LIBRARIES( bin_format_it LINK_PUBLIC double-conversion format_it)

