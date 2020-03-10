add_custom_command(OUTPUT FallbackConfiguration.cpp FallbackConfiguration.h
	COMMAND config2cpp-exe -cfg ${CMAKE_CURRENT_SOURCE_DIR}/FallbackConfiguration.cfg -class FallbackConfiguration -singleton
	DEPENDS config2cpp-exe FallbackConfiguration.cfg
)
add_executable(demo-encapsulate-lookup-api
	FooConfiguration.cpp
	${CMAKE_CURRENT_BINARY_DIR}/FallbackConfiguration.cpp
	main.cpp
)
target_include_directories(demo-encapsulate-lookup-api PRIVATE ${CMAKE_CURRENT_BINARY_DIR})
target_link_libraries(demo-encapsulate-lookup-api PUBLIC config4cpp)
