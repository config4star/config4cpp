add_executable(demo-recipe
	RecipeFileParser.cpp main.cpp
)
target_link_libraries(demo-recipe PUBLIC config4cpp)
