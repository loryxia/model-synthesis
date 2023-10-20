cmake_minimum_required(VERSION 3.1)

project(ModelSynthesis)

set_property(GLOBAL PROPERTY CXX_STANDARD 98)

option(_XMLWIDECHAR "char set portable" ON)

file(GLOB SOURCES *.h *.cpp
    src/*.h src/*.cpp
    src/parseInput/*.h src/parseInput/*.cpp
    src/propagator/*.h src/propagator/*.cpp
    src/third_party/*.h src/third_party/*.cpp
    src/third_party/lodepng/*.h src/third_party/lodepng/*.cpp)

if(_XMLWIDECHAR)
    add_definitions(-D_XMLWIDECHAR)
endif()

message(status ${CMAKE_BINARY_DIR})
message(status ${CMAKE_CURRENT_BINARY_DIR})
message(status ${CMAKE_CURRENT_SOURCE_DIR})
message(status ${ConfigurationName})

include_directories(.)
add_executable(ModelSynthesis ${SOURCES})

file(COPY samples.xml DESTINATION ${CMAKE_CURRENT_BINARY_DIR})
file(COPY "samples large.xml" DESTINATION ${CMAKE_CURRENT_BINARY_DIR})
file(COPY samples DESTINATION ${CMAKE_CURRENT_BINARY_DIR})

