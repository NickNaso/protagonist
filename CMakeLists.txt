cmake_minimum_required(VERSION 3.0)

ADD_SUBDIRECTORY(drafter)

include_directories(
  "drafter/ext/snowcrash/ext/markdown-parser/ext/sundown/src"
  "drafter/ext/snowcrash/ext/markdown-parser/src"
  "drafter/ext/snowcrash/src"
  "drafter/ext/sos/src"
  "drafter/ext/cmdline"
  "drafter/src/refract"
  "drafter/src"
)


project(protagonist)

file(GLOB SOURCE_FILES "src/*.cc" "src/*.h")
add_library(${PROJECT_NAME} SHARED ${SOURCE_FILES})

set_target_properties(${PROJECT_NAME} PROPERTIES PREFIX "" SUFFIX ".node")
target_include_directories(${PROJECT_NAME} PRIVATE ${CMAKE_JS_INC})
target_link_libraries(${PROJECT_NAME} ${CMAKE_JS_LIB})
target_link_libraries(${PROJECT_NAME} libdrafter)
