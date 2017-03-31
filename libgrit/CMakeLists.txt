cmake_minimum_required (VERSION 2.8.2)
project (libgrit)

# The version number.
set (GRIT_VERSION_MAJOR 0)
set (GRIT_VERSION_MINOR 1)
set (GRIT_VERSION_PATCH 1)

# Configuration file to pass settings to project source code.
configure_file (
  "${PROJECT_SOURCE_DIR}/BuildConfig.h.in"
  "${PROJECT_BINARY_DIR}/BuildConfig.h"
  )

# Set compiler-specific flags
if ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "Clang" OR
    "${CMAKE_CXX_COMPILER_ID}" STREQUAL "GNU")
  add_definitions(-std=c++14)
  set(warnings "-Wall -Wextra -Werror")
endif()

# Add the binary tree to the search path for include files
# so that we will find the build config file.
include_directories("${PROJECT_BINARY_DIR}")

# GTest
enable_testing()
find_package(GTest REQUIRED)
include_directories(${GTEST_INCLUDE_DIRS})

#add_executable(tests tests.cpp)
#target_link_libraries(tests ${GTEST_BOTH_LIBRARIES})