add_executable(demo-log-level
	FooConfiguration.cpp
	Logger.cpp
	A.cpp
	B.cpp
	main.cpp
)
target_link_libraries(demo-log-level PUBLIC config4cpp)
