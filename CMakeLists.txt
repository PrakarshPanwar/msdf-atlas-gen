# MSDF atlas gen Subdirectory
file(GLOB_RECURSE MSDF_LIB_SOURCES
		CONFIGURE_DEPENDS
		${CMAKE_CURRENT_SOURCE_DIR}/msdf-atlas-gen/*.cpp
		${CMAKE_CURRENT_SOURCE_DIR}/msdf-atlas-gen/*.hpp
		${CMAKE_CURRENT_SOURCE_DIR}/msdf-atlas-gen/*.h
	)

# Add MSDF gen library
add_subdirectory(msdfgen)

# Create library
add_library(msdf-atlas-gen ${MSDF_LIB_SOURCES})

# Linking MSDF gen
target_link_libraries(msdf-atlas-gen
		msdfgen
	)

target_include_directories(msdf-atlas-gen PUBLIC
		${CMAKE_CURRENT_SOURCE_DIR}/msdf-atlas-gen
		${CMAKE_CURRENT_SOURCE_DIR}/msdfgen
		${CMAKE_CURRENT_SOURCE_DIR}/msdfgen/include
	)

target_compile_definitions(msdf-atlas-gen
		PUBLIC MSDF_ATLAS_NO_ARTERY_FONT
	)
