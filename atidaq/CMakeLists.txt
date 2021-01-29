ExternalProject_Add(
	atidaq
	#GIT_REPOSITORY https://github.com/roboticslibrary/atidaq.git
	#GIT_TAG cmake-1.0.6
	URL https://github.com/roboticslibrary/atidaq/archive/cmake-1.0.6.tar.gz
	#URL ${CMAKE_CURRENT_SOURCE_DIR}/atidaq-cmake-1.0.6.tar.gz
	URL_MD5 9859eee3baedc989268fd9052c2341af
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
	atidaq install-licenses
	DEPENDEES install
	COMMAND ${CMAKE_COMMAND} -E copy <SOURCE_DIR>/readme.txt ${CMAKE_INSTALL_FULL_DATADIR}/licenses/atidaq/readme.txt
)
