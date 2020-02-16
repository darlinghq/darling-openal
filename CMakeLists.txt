project(OpenAL)

set(DYLIB_COMPAT_VERSION "1.0.0")
set(DYLIB_CURRENT_VERSION "1.0.0")

include_directories(
	${CMAKE_CURRENT_SOURCE_DIR}/Source/OpenAL
	${CMAKE_CURRENT_SOURCE_DIR}/Source/OpenAL/al
	${CMAKE_CURRENT_SOURCE_DIR}/extra
	${CMAKE_SOURCE_DIR}/src/frameworks
)
include_directories(BEFORE ${CMAKE_SOURCE_DIR}/src/external/libcxx/include)

add_definitions(-DSizeOf32=sizeof)

set(openal_sources
	Source/OpenAL/oalBuffer.cpp
	Source/OpenAL/oalCaptureDevice.cpp
	Source/OpenAL/oalCaptureMixer.cpp
	Source/OpenAL/oalContext.cpp
	Source/OpenAL/oalDevice.cpp
	Source/OpenAL/oalImp.cpp
	Source/OpenAL/oalOSX.cpp
	Source/OpenAL/oalRingBuffer.cpp
	Source/OpenAL/oalSource.cpp
	extra/CAStreamBasicDescription.cpp
	extra/CAXException.cpp
)

add_framework(OpenAL
    FAT
    CURRENT_VERSION
    VERSION "A"

    SOURCES
        ${openal_sources}

    DEPENDENCIES
        system
		cxx
)

