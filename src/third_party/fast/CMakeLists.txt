project(fast)
file(GLOB_RECURSE C_FILES ${CMAKE_CURRENT_SOURCE_DIR} *.c)
set_source_files_properties(${C_FILES} PROPERTIES LANGUAGE CXX)
add_library(fast ${C_FILES})
set_property(TARGET fast PROPERTY FOLDER OpenMVG/3rdParty)

if(FAST_INCLUDE_INSTALL_DIR)
  set(INCLUDE_INSTALL_DIR ${FAST_INCLUDE_INSTALL_DIR})
else()
  set(INCLUDE_INSTALL_DIR "${CMAKE_INSTALL_PREFIX}/include/fast")
endif()

install(
  DIRECTORY .
  DESTINATION ${INCLUDE_INSTALL_DIR}
  COMPONENT headers
  FILES_MATCHING PATTERN "*.h"
)
install(TARGETS fast DESTINATION lib EXPORT openMVG-targets)
