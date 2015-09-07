cmake_minimum_required(VERSION 2.8.11)

project(config4cpp)
set(PROJECT_VERSION 1.1-dev)

message(STATUS "~~~ ${PROJECT_NAME} ${PROJECT_VERSION} ~~~")

option(BUILD_SCHEMA_TESTS "Build Schema tests." OFF)


add_definitions(-Wall -Wextra -pedantic)

include_directories("include")

subdirs(src)

if( BUILD_SCHEMA_TESTS )
    subdirs(tests/schema-types)
endif()
