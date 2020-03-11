set(DEMOS_LIST
	encapsulate-lookup-api
	extended-schema-validator
	log-level
	recipes
	simple-encapsulation
)

foreach(DEMO ${DEMOS_LIST})
	add_subdirectory(${DEMO})
endforeach(DEMO)
