add_executable(demo-extended-schema-validator FooConfiguration.cpp SchemaTypeHex.cpp main.cpp)
target_link_libraries(demo-extended-schema-validator PUBLIC config4cpp)
