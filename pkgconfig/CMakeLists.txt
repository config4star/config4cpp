configure_file(config4cpp.pc.in config4cpp.pc @ONLY)
install(
	FILES ${CMAKE_CURRENT_BINARY_DIR}/config4cpp.pc
	DESTINATION lib/pkgconfig
)
