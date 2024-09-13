ExternalProject_Add(
	superglu
	#GIT_REPOSITORY https://github.com/coin3d/superglu.git
	#GIT_TAG v1.3.2
	URL https://github.com/coin3d/superglu/releases/download/v1.3.2/superglu-1.3.2-src.tar.gz
	#URL ${CMAKE_CURRENT_SOURCE_DIR}/superglu-1.3.2-src.tar.gz
	URL_MD5 3ee85c260592967f68f67db7ddb58caa
	CMAKE_ARGS
		-DCMAKE_BUILD_TYPE=${CMAKE_BUILD_TYPE}
		-DCMAKE_CFG_INTDIR=${CMAKE_CFG_INTDIR}
		-DCMAKE_INSTALL_PREFIX=${CMAKE_INSTALL_PREFIX}
		-DCMAKE_PREFIX_PATH=${CMAKE_PREFIX_PATH}
		-DCMAKE_TRY_COMPILE_CONFIGURATION=${CMAKE_TRY_COMPILE_CONFIGURATION}
	INSTALL_DIR ${CMAKE_INSTALL_PREFIX}
)

ExternalProject_Add_Step(
	superglu install-licenses
	DEPENDEES install
	COMMAND ${CMAKE_COMMAND} -E copy <SOURCE_DIR>/COPYING ${CMAKE_INSTALL_FULL_DATADIR}/licenses/superglu/COPYING
)
