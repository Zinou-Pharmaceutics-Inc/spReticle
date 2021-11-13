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

# Build plugin
build_plugin()

install(
    FILES
        ${CMAKE_CURRENT_BINARY_DIR}/spReticleLoc${SUFFIX_NAME}
        ${CMAKE_SOURCE_DIR}/spReticleLoc.mel
        ${CMAKE_SOURCE_DIR}/AEspReticleLocTemplate.mel
    DESTINATION
        ${CMAKE_SOURCE_DIR}/install
)
