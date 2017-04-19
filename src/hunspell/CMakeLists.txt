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

add_library(${libname}
	${lib_sources})

add_definitions(-DBUILDING_LIBHUNSPELL)

set_target_properties(${libname} PROPERTIES PUBLIC_HEADER "${lib_headers}")
set_property(TARGET ${libname} PROPERTY XCODE_ATTRIBUTE_CLANG_CXX_LIBRARY "libc++")

install(TARGETS ${libname}
	ARCHIVE DESTINATION lib
	LIBRARY DESTINATION lib
	RUNTIME DESTINATION bin
	PUBLIC_HEADER DESTINATION include)
