cmake_minimum_required (VERSION 3.0)
set(CONFIG4CPP_VERSION_MAJOR 1)
set(CONFIG4CPP_VERSION_MINOR 1)
project(CONFIG4CPP
	VERSION ${CONFIG4CPP_VERSION_MAJOR}.${CONFIG4CPP_VERSION_MINOR}
)
include(GNUInstallDirs)

# Shadow build enforced to not overwrite existing Makefiles
if(${CMAKE_SOURCE_DIR} STREQUAL ${CMAKE_BINARY_DIR})
	message(FATAL_ERROR "Shadow build is required. Please create a separate build directory and run 'cmake /path/to/config4cpp/source' there.")
endif()

# Build options
option(BUILD_TESTS "Build tests" ON)
option(BUILD_DEMOS "Build demos" OFF)
option(BUILD_STATIC "Build a copy of statically compiled library" OFF)

# Compiler options
set(CMAKE_CXX_STANDARD 98)
include_directories(include)

# Library and binary sources
add_subdirectory(src)

if (BUILD_TESTS)
	enable_testing()
	# Tests
	add_subdirectory(tests/schema-types)
endif()

if (BUILD_DEMOS)
	add_subdirectory(demos)
endif()

# pkgconfig for apps that uses this library
add_subdirectory(pkgconfig)
