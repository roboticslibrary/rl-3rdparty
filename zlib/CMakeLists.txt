ExternalProject_Add(
	zlib
	#GIT_REPOSITORY https://github.com/roboticslibrary/zlib.git
	#GIT_TAG cmake-1.2.11
	URL https://github.com/roboticslibrary/zlib/archive/cmake-1.2.11.tar.gz
	#URL ${CMAKE_CURRENT_SOURCE_DIR}/zlib-cmake-1.2.11.tar.gz
	URL_MD5 6902c1522e9ed4717dffb368e250fe4f
	CMAKE_ARGS
		-DCMAKE_BUILD_TYPE=${CMAKE_BUILD_TYPE}
		-DCMAKE_CFG_INTDIR=${CMAKE_CFG_INTDIR}
		-DCMAKE_INSTALL_PREFIX=${CMAKE_INSTALL_PREFIX}
		-DCMAKE_PREFIX_PATH=${CMAKE_PREFIX_PATH}
		-DCMAKE_TRY_COMPILE_CONFIGURATION=${CMAKE_TRY_COMPILE_CONFIGURATION}
	INSTALL_DIR ${CMAKE_INSTALL_PREFIX}
)

ExternalProject_Add_Step(
	zlib install-licenses
	DEPENDEES install
	COMMAND ${CMAKE_COMMAND} -E copy <SOURCE_DIR>/README ${CMAKE_INSTALL_FULL_DATADIR}/licenses/zlib/README
)
