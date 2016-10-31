cmake_minimum_required(VERSION 3.2)

project(JPEGWrapper)

if (NOT CMAKE_BUILD_TYPE)
  message(STATUS "No build type selected, defaulting to Release")
  set(CMAKE_BUILD_TYPE "Release")
endif()

set(CMAKE_MODULE_PATH ${CMAKE_HOME_DIRECTORY}/cmake ${CMAKE_MODULE_PATH})

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

include_directories(src)

file(GLOB_RECURSE SRC RELATIVE ${PROJECT_SOURCE_DIR} src/*.cpp)
file(GLOB_RECURSE HEADERS RELATIVE ${PROJECT_SOURCE_DIR} src/*.h)

add_library(jpegwrapper ${HEADERS} ${SRC})

install(TARGETS jpegwrapper
  EXPORT JPEGWrapperTarget
  ARCHIVE DESTINATION lib)

install(DIRECTORY src/ DESTINATION include/jpegwrapper
        FILES_MATCHING PATTERN "*.h")
