cmake_minimum_required(VERSION 2.6)

project(POVRay CXX)

add_definitions(-DDISTRIBUTION_MESSAGE_2="xx")

include_directories(
    source
    vfe
    libraries/boost
    libraries/jpeg
    libraries/openexr/IlmImf
    libraries/ilmbase/Imath
    libraries/ilmbase/Iex
    libraries/ilmbase/Half
    libraries/png
    libraries/tiff/libtiff
    libraries/zlib
)
if(WIN32)
    include_directories(vfe/win)
else()
    include_directories(vfe/unix)
endif()

if(WIN32)
    add_definitions(-D_CRT_SECURE_NO_DEPRECATE)
    add_definitions(-DNON_UNIX_OPENEXR_HEADERS)
endif()

add_subdirectory(source/base)
