ExternalProject_Add(
	solid3
	#GIT_REPOSITORY https://github.com/dtecta/solid3.git
	#GIT_TAG cbac1402da5df65e7239558a6c04feb736e54b27
	URL https://github.com/dtecta/solid3/archive/cbac1402da5df65e7239558a6c04feb736e54b27.zip
	#URL ${CMAKE_CURRENT_SOURCE_DIR}/solid3-cbac1402da5df65e7239558a6c04feb736e54b27.tar.gz
	URL_MD5 b566a0732d8c267b0d65b461914d6fc0
	CMAKE_ARGS
		-DBUILD_EXAMPLES=OFF
		-DCMAKE_BUILD_TYPE=${CMAKE_BUILD_TYPE}
		-DCMAKE_CFG_INTDIR=${CMAKE_CFG_INTDIR}
		-DCMAKE_INSTALL_PREFIX=${CMAKE_INSTALL_PREFIX}
		-DCMAKE_PREFIX_PATH=${CMAKE_PREFIX_PATH}
		-DCMAKE_TRY_COMPILE_CONFIGURATION=${CMAKE_TRY_COMPILE_CONFIGURATION}
		-DDYNAMIC_SOLID=${BUILD_SHARED_LIBS}
		-DUSE_DOUBLES=ON
	INSTALL_DIR ${CMAKE_INSTALL_PREFIX}
)

ExternalProject_Add_Step(
	solid3 install-licenses
	DEPENDEES install
	COMMAND ${CMAKE_COMMAND} -E copy <SOURCE_DIR>/LICENSE_GPL.txt ${CMAKE_INSTALL_FULL_DATADIR}/licenses/solid3/LICENSE_GPL.txt
	COMMAND ${CMAKE_COMMAND} -E copy <SOURCE_DIR>/LICENSE_QPL.txt ${CMAKE_INSTALL_FULL_DATADIR}/licenses/solid3/LICENSE_QPL.txt
	COMMAND ${CMAKE_COMMAND} -E copy <SOURCE_DIR>/README.md ${CMAKE_INSTALL_FULL_DATADIR}/licenses/solid3/README.md
)
