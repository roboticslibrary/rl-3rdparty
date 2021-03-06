ExternalProject_Add(
	eigen3
	#GIT_REPOSITORY https://gitlab.com/libeigen/eigen.git
	#GIT_TAG 3.3.9
	URL https://gitlab.com/libeigen/eigen/-/archive/3.3.9/eigen-3.3.9.tar.gz
	#URL ${CMAKE_CURRENT_SOURCE_DIR}/eigen-3.3.9.tar.gz
	URL_MD5 609286804b0f79be622ccf7f9ff2b660
	CMAKE_ARGS
		-DBUILD_TESTING=OFF
		-DCMAKE_BUILD_TYPE=${CMAKE_BUILD_TYPE}
		-DCMAKE_CFG_INTDIR=${CMAKE_CFG_INTDIR}
		-DCMAKE_INSTALL_PREFIX=${CMAKE_INSTALL_PREFIX}
		-DCMAKE_PREFIX_PATH=${CMAKE_PREFIX_PATH}
		-DCMAKE_TRY_COMPILE_CONFIGURATION=${CMAKE_TRY_COMPILE_CONFIGURATION}
		-DEIGEN_TEST_NOQT=ON
	INSTALL_DIR ${CMAKE_INSTALL_PREFIX}
)

ExternalProject_Add_Step(
	eigen3 install-licenses
	DEPENDEES install
	COMMAND ${CMAKE_COMMAND} -E copy <SOURCE_DIR>/COPYING.BSD ${CMAKE_INSTALL_FULL_DATADIR}/licenses/eigen3/COPYING.BSD
	COMMAND ${CMAKE_COMMAND} -E copy <SOURCE_DIR>/COPYING.GPL ${CMAKE_INSTALL_FULL_DATADIR}/licenses/eigen3/COPYING.GPL
	COMMAND ${CMAKE_COMMAND} -E copy <SOURCE_DIR>/COPYING.LGPL ${CMAKE_INSTALL_FULL_DATADIR}/licenses/eigen3/COPYING.LGPL
	COMMAND ${CMAKE_COMMAND} -E copy <SOURCE_DIR>/COPYING.MINPACK ${CMAKE_INSTALL_FULL_DATADIR}/licenses/eigen3/COPYING.MINPACK
	COMMAND ${CMAKE_COMMAND} -E copy <SOURCE_DIR>/COPYING.MPL2 ${CMAKE_INSTALL_FULL_DATADIR}/licenses/eigen3/COPYING.MPL2
	COMMAND ${CMAKE_COMMAND} -E copy <SOURCE_DIR>/COPYING.README ${CMAKE_INSTALL_FULL_DATADIR}/licenses/eigen3/COPYING.README
)
