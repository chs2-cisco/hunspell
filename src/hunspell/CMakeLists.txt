set(libname hunspell)

set(lib_sources
	affentry.cxx affixmgr.cxx csutil.cxx
	hashmgr.cxx hunspell.cxx suggestmgr.cxx
	phonet.cxx filemgr.cxx hunzip.cxx replist.cxx
	affentry.hxx htypes.hxx affixmgr.hxx
	csutil.hxx atypes.hxx suggestmgr.hxx
	baseaffix.hxx hashmgr.hxx langnum.hxx
	phonet.hxx filemgr.hxx hunzip.hxx replist.hxx)

set(lib_headers
	hunspell.hxx hunspell.h hunvisapi.h
	w_char.hxx atypes.hxx csutil.hxx htypes.hxx)

add_library(${libname} SHARED
	${lib_sources})

add_definitions(-DBUILDING_LIBHUNSPELL)

if (APPLE)
	set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -stdlib=libc++")
	set(CMAKE_OSX_ARCHITECTURES x86_64)
endif()

set_target_properties(${libname} PROPERTIES PUBLIC_HEADER "${lib_headers}")

install(TARGETS ${libname}
	ARCHIVE DESTINATION lib
	LIBRARY DESTINATION lib
	RUNTIME DESTINATION bin
	PUBLIC_HEADER DESTINATION include)
