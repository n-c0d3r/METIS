# Add this directory for internal users.
include_directories(.)

# Find sources.
file(GLOB metis_sources *.c)

# Build libmetis.
add_library(metis ${METIS_LIBRARY_TYPE} ${metis_sources})
target_link_libraries(metis GKlib)
target_include_directories(metis 
  PUBLIC 
    ${CMAKE_CURRENT_LIST_DIR}/../GKlib
    ${CMAKE_CURRENT_LIST_DIR}/../include
)

if(METIS_INSTALL)
  install(TARGETS metis
    LIBRARY DESTINATION lib
    RUNTIME DESTINATION lib
    ARCHIVE DESTINATION lib)
endif()
