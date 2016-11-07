set(OFX_SUPPORT_HEADER_DIR "${CMAKE_CURRENT_SOURCE_DIR}/include")
set(OFX_SUPPORT_LIBRARY_DIR "${CMAKE_CURRENT_SOURCE_DIR}/Library")

file(GLOB_RECURSE OFX_SUPPORT_HEADER_FILES "${OFX_SUPPORT_HEADER_DIR}/*.h")
#file(GLOB_RECURSE OFX_SUPPORT_LIBRARY_FILES "${OFX_SUPPORT_LIBRARY_DIR}/*.cpp")
set(OFX_SUPPORT_LIBRARY_FILES "${OFX_SUPPORT_LIBRARY_DIR}/ofxsMultiThread.cpp;${OFX_SUPPORT_LIBRARY_DIR}/ofxsInteract.cpp;${OFX_SUPPORT_LIBRARY_DIR}/ofxsProperty.cpp;${OFX_SUPPORT_LIBRARY_DIR}/ofxsLog.cpp;${OFX_SUPPORT_LIBRARY_DIR}/ofxsCore.cpp;${OFX_SUPPORT_LIBRARY_DIR}/ofxsPropertyValidation.cpp;${OFX_SUPPORT_LIBRARY_DIR}/ofxsImageEffect.cpp;${OFX_SUPPORT_LIBRARY_DIR}/ofxsParams.cpp")

# Create OfxSupport static lib
add_library(OfxSupport STATIC ${OFX_HEADER_FILES} ${OFX_SUPPORT_HEADER_FILES} ${OFX_SUPPORT_LIBRARY_FILES})
set_target_properties(OfxSupport PROPERTIES LINKER_LANGUAGE CXX)
if(NOT MSVC)
	set_target_properties(OfxSupport PROPERTIES COMPILE_FLAGS "-fPIC")
endif()
target_include_directories(OfxSupport PUBLIC ${OFX_HEADER_DIR} ${OFX_SUPPORT_HEADER_DIR})

# Install OfxSupport headers and library
#install(
#    FILES ${OFX_SUPPORT_HEADER_FILES}
#    DESTINATION "include"
#)
#install(TARGETS OfxSupport DESTINATION "lib" OPTIONAL)
