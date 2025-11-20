file (GLOB HEADERS "*.h")
file (GLOB SOURCES "[^_]*.cpp")

set(BIN texrecon)

add_executable(${BIN} ${SOURCES})
set_property(TARGET ${BIN} PROPERTY INTERPROCEDURAL_OPTIMIZATION True)
add_dependencies(${BIN} ext_mve)
include_directories(${TBB_INCLUDE_DIRS})
message(STATUS "MVE_MVE_LIBRARY = ${MVE_MVE_LIBRARY}")
message(STATUS "MVE_UTIL_LIBRARY = ${MVE_UTIL_LIBRARY}")
target_link_libraries(${BIN} tex ${TBB_LIBRARIES} ${MVE_MVE_LIBRARY} ${MVE_UTIL_LIBRARY})
install(TARGETS ${BIN} RUNTIME DESTINATION bin)
