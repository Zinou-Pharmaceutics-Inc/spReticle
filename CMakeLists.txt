cmake_minimum_required(VERSION 2.8)

include($ENV{DEVKIT_LOCATION}/cmake/pluginEntry.cmake)

set(PROJECT_NAME spReticleLoc)

set(SOURCE_FILES
   spReticleLoc.cpp
   GPURenderer.cpp
   V2Renderer.cpp
)

set(LIBRARIES
     OpenMaya
     OpenMayaUI
     OpenMayaRender
     Foundation
)

if(MSVC)
elseif(APPLE)
else()
    # From original Makefile, probably not necessary
    set(CMAKE_CXX_FLAGS "-fPIC")
    set(CMAKE_CXX_FLAGS_RELEASE ${CMAKE_CXX_FLAGS} "-O3")
    set(CMAKE_CXX_FLAGS_DEBUG "-g -gstabs+")
endif()


# Build plugin
build_plugin()
