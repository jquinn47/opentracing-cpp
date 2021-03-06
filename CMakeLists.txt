cmake_minimum_required (VERSION 2.8)
set(PROJECT_NAME "opentracing")
project (${PROJECT_NAME})

set(lib_major_version "2")
set(lib_minor_version "0")
set(lib_patch_version "0")
set(opentracing_version "${lib_major_version}.${lib_minor_version}.${lib_patch_version}")
set(opentracing_url "https://github.com/opentracing/opentracing-cpp")

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

option(enable_noop "Build noop tracer." OFF)
option(enable_tests "Build unit tests." OFF)

add_subdirectory(opentracing)

if(enable_tests)
    enable_testing()
    add_subdirectory(thirdparty/googletest/googletest)
    add_subdirectory(test)
endif()
