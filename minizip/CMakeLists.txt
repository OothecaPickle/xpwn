INCLUDE(FindZLIB)

IF(NOT ZLIB_FOUND)
	message(FATAL_ERROR "zlib is required for libminizip!")
ENDIF(NOT ZLIB_FOUND)

add_definitions( -DNOCRYPT -DNOUNCRYPT )

include_directories(${ZLIB_INCLUDE_DIR})
link_directories(${ZLIB_LIBRARIES})

add_library(minizip ioapi.c unzip.c zip.c)

target_link_libraries(minizip z)

install(TARGETS minizip DESTINATION bin)
