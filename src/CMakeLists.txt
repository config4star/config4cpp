add_library(config4cpp SchemaLex.cpp
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


add_executable(config2cpp config2cpp-main.cpp
                            Config2Cpp.cpp
                            )
target_link_libraries(config2cpp config4cpp)


add_executable(config2cpp-nocheck config2cpp-nocheck-main.cpp
                                    Config2Cpp.cpp
                                    )
target_link_libraries(config2cpp-nocheck config4cpp)


add_executable(config4cpp-bin config4cpp.cpp)
target_link_libraries(config4cpp-bin config4cpp)



install(TARGETS config4cpp
                LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
                ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
                RUNTIME DESTINATION ${CMAKE_INSTALL_LIBDIR}
                )
install(DIRECTORY ../include/config4cpp
                DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
                )

