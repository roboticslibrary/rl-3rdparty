ExternalProject_Add(
	boost
	URL https://github.com/boostorg/boost/releases/download/boost-1.86.0/boost-1.86.0-cmake.7z
	#URL ${CMAKE_CURRENT_SOURCE_DIR}/boost-1.86.0-cmake.7z
	URL_MD5 c33bf9137ff5ff1d3d0f28af212c9704
	CMAKE_ARGS
		-DBUILD_SHARED_LIBS=${BUILD_SHARED_LIBS}
		-DCMAKE_BUILD_TYPE=${CMAKE_BUILD_TYPE}
		-DCMAKE_CFG_INTDIR=${CMAKE_CFG_INTDIR}
		-DCMAKE_INSTALL_PREFIX=${CMAKE_INSTALL_PREFIX}
		-DCMAKE_PREFIX_PATH=${CMAKE_PREFIX_PATH}
		-DCMAKE_TRY_COMPILE_CONFIGURATION=${CMAKE_TRY_COMPILE_CONFIGURATION}
	INSTALL_DIR ${CMAKE_INSTALL_PREFIX}
)

ExternalProject_Add_Step(
	boost install-licenses
	DEPENDEES install
	COMMAND ${CMAKE_COMMAND} -E copy <SOURCE_DIR>/LICENSE_1_0.txt ${CMAKE_INSTALL_FULL_DATADIR}/licenses/boost/LICENSE_1_0.txt
)
