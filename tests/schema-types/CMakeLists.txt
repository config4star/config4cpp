add_executable(test-schema-types-exe main.cpp)
set_target_properties(test-schema-types-exe
	PROPERTIES OUTPUT_NAME test-schema-types
)
target_link_libraries(test-schema-types-exe PUBLIC config4cpp)

add_test(NAME TEST_SCHEMA_TYPES
	COMMAND ${CMAKE_CURRENT_BINARY_DIR}/test-schema-types -cfg ${CMAKE_CURRENT_SOURCE_DIR}/schema-type-tests.cfg
)
