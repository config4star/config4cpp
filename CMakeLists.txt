cmake_minimum_required(VERSION 2.8.11)

project(config4cpp)
set(PROJECT_VERSION 1.1-dev)

message(STATUS "~~~ ${PROJECT_NAME} ${PROJECT_VERSION} ~~~")


add_definitions(-Wall -Wextra -pedantic)

include_directories("include")

subdirs(src)
subdirs(tests/schema-types)
