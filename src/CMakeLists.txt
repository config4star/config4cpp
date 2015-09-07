
set(LIB_SRC SchemaLex.cpp
			SchemaParser.cpp
			MBChar.cpp
			SchemaValidator.cpp
			platform.cpp
			util.cpp
			Configuration.cpp
			DefaultSecurity.cpp
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

add_library(libconfig4cpp ${LIB_SRC})
set_target_properties(libconfig4cpp PROPERTIES PREFIX "")


set(CONFIG2CPP_SRC config2cpp-main.cpp
                    Config2Cpp.cpp
                    )

add_executable(config2cpp ${CONFIG2CPP_SRC})
target_link_libraries(config2cpp libconfig4cpp)


set(CONFIG2CPP_NOCHECK_SRC config2cpp-nocheck-main.cpp
                            Config2Cpp.cpp
                            )

add_executable(config2cpp-nocheck ${CONFIG2CPP_NOCHECK_SRC})
target_link_libraries(config2cpp-nocheck libconfig4cpp)


set(CONFIG4CPP_SRC config4cpp.cpp)

add_executable(config4cpp-bin ${CONFIG4CPP_SRC})
target_link_libraries(config4cpp-bin libconfig4cpp)
