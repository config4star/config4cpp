add_executable(config2cpp-nocheck-exe
	config2cpp-nocheck-main.cpp
	Config2Cpp.cpp
)
set_target_properties(config2cpp-nocheck-exe
	PROPERTIES OUTPUT_NAME config2cpp-nocheck
)

add_custom_command(
	OUTPUT DefaultSecurity.cpp DefaultSecurity.h
	COMMAND ${CMAKE_CURRENT_BINARY_DIR}/config2cpp-nocheck -cfg ${CMAKE_CURRENT_SOURCE_DIR}/DefaultSecurity.cfg -class DefaultSecurity -namespace CONFIG4CPP_NAMESPACE
	DEPENDS config2cpp-nocheck-exe
	WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
)

set(LIB_SOURCES
	SchemaLex.cpp
	SchemaParser.cpp
	MBChar.cpp
	SchemaValidator.cpp
	platform.cpp
	util.cpp
	Configuration.cpp
	${CMAKE_CURRENT_BINARY_DIR}/DefaultSecurity.cpp
	DefaultSecurityConfiguration.cpp
	ConfigurationException.cpp
	ConfigurationImpl.cpp
	ConfigParser.cpp
	UidIdentifierProcessor.cpp
	ConfigScope.cpp
	ConfigScopeEntry.cpp
	ConfigItem.cpp
	LexToken.cpp
	LexBase.cpp
	ConfigLex.cpp
	StringBuffer.cpp
	StringVector.cpp
	SchemaType.cpp
	SchemaTypeBoolean.cpp
	SchemaTypeDurationMicroseconds.cpp
	SchemaTypeDurationMilliseconds.cpp
	SchemaTypeDurationSeconds.cpp
	SchemaTypeEnum.cpp
	SchemaTypeFloat.cpp
	SchemaTypeFloatWithUnits.cpp
	SchemaTypeInt.cpp
	SchemaTypeIntWithUnits.cpp
	SchemaTypeMemorySizeBytes.cpp
	SchemaTypeMemorySizeKB.cpp
	SchemaTypeMemorySizeMB.cpp
	SchemaTypeScope.cpp
	SchemaTypeString.cpp
	SchemaTypeUnitsWithFloat.cpp
	SchemaTypeUnitsWithInt.cpp
	SchemaTypeList.cpp
	SchemaTypeTable.cpp
	SchemaTypeTuple.cpp
	SchemaTypeTypedef.cpp
)

add_library(config4cpp SHARED ${LIB_SOURCES})
if(BUILD_STATIC)
	add_library(config4cpp-static STATIC ${LIB_SOURCES})
	set_target_properties(config4cpp-static
		PROPERTIES OUTPUT_NAME config4cpp
	)
install(TARGETS config4cpp-static)
endif()
file(GLOB CONFIG4CPP_PUB_HDR
	${CMAKE_SOURCE_DIR}/include/config4cpp/*.h
)
set_target_properties(config4cpp PROPERTIES
	PUBLIC_HEADER "${CONFIG4CPP_PUB_HDR}"
	SOVERSION ${CONFIG4CPP_VERSION_MAJOR}
	VERSION ${PROJECT_VERSION}
)
install(TARGETS config4cpp
	LIBRARY DESTINATION lib
	PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/config4cpp
)

add_executable(config2cpp-exe
	config2cpp-main.cpp
	Config2Cpp.cpp
)
target_link_libraries(config2cpp-exe config4cpp)
set_target_properties(config2cpp-exe
	PROPERTIES OUTPUT_NAME config2cpp
)
install(TARGETS config2cpp-exe)

add_executable(config4cpp-exe
	config4cpp.cpp
)
target_link_libraries(config4cpp-exe config4cpp)
set_target_properties(config4cpp-exe
	PROPERTIES OUTPUT_NAME config4cpp
)
install(TARGETS config4cpp-exe)
