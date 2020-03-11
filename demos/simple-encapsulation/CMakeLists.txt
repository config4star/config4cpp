add_custom_command(OUTPUT FallbackConfiguration.cpp
	COMMAND config2cpp-exe -cfg ${CMAKE_CURRENT_SOURCE_DIR}/FallbackConfiguration.cfg -class FallbackConfiguration -singleton
	DEPENDS config2cpp-exe FallbackConfiguration.cfg
)
add_executable(demo-simple-encapsulation
	FooConfiguration.cpp
	${CMAKE_CURRENT_BINARY_DIR}/FallbackConfiguration.cpp
	main.cpp
)
target_include_directories(demo-simple-encapsulation PRIVATE ${CMAKE_CURRENT_BINARY_DIR})
target_link_libraries(demo-simple-encapsulation PUBLIC config4cpp)
