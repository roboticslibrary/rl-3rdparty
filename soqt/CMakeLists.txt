ExternalProject_Add(
	soqt
	DEPENDS coin
	#GIT_REPOSITORY https://github.com/coin3d/soqt.git
	#GIT_TAG SoQt-1.6.2
	URL https://github.com/coin3d/soqt/releases/download/v1.6.2/soqt-1.6.2-src.tar.gz
	#URL ${CMAKE_CURRENT_SOURCE_DIR}/soqt-SoQt-1.6.2.zip
	URL_MD5 70ef0990e009d806c59941d819a62c98
	CMAKE_ARGS
		-DCMAKE_BUILD_TYPE=${CMAKE_BUILD_TYPE}
		-DCMAKE_CFG_INTDIR=${CMAKE_CFG_INTDIR}
		-DCMAKE_INSTALL_PREFIX=${CMAKE_INSTALL_PREFIX}
		-DCMAKE_PREFIX_PATH=${CMAKE_PREFIX_PATH}
		-DCMAKE_TRY_COMPILE_CONFIGURATION=${CMAKE_TRY_COMPILE_CONFIGURATION}
		-DSOQT_BUILD_DOCUMENTATION=OFF
		-DSOQT_BUILD_SHARED_LIBS=${BUILD_SHARED_LIBS}
		-DSOQT_BUILD_TESTS=OFF
		-DSOQT_USE_QT5=${RL_USE_QT5}
		-DSOQT_USE_QT6=${RL_USE_QT6}
	INSTALL_DIR ${CMAKE_INSTALL_PREFIX}
)

ExternalProject_Add_Step(
	soqt install-licenses
	DEPENDEES install
	COMMAND ${CMAKE_COMMAND} -E copy <SOURCE_DIR>/COPYING ${CMAKE_INSTALL_FULL_DATADIR}/licenses/soqt/COPYING
)
