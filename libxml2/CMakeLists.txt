ExternalProject_Add(
	libxml2
	DEPENDS libiconv
	#GIT_REPOSITORY https://gitlab.gnome.org/GNOME/libxml2.git
	#GIT_TAG v2.13.3
	URL https://gitlab.gnome.org/GNOME/libxml2/-/archive/v2.13.3/libxml2-v2.13.3.tar.gz
	#URL ${CMAKE_CURRENT_SOURCE_DIR}/libxml2-v2.13.3.tar.gz
	URL_MD5 f312e123df5096472359b430836f653e
	CMAKE_ARGS
		-DBUILD_SHARED_LIBS=${BUILD_SHARED_LIBS}
		-DCMAKE_BUILD_TYPE=${CMAKE_BUILD_TYPE}
		-DCMAKE_CFG_INTDIR=${CMAKE_CFG_INTDIR}
		-DCMAKE_FIND_PACKAGE_PREFER_CONFIG=ON
		-DCMAKE_INSTALL_PREFIX=${CMAKE_INSTALL_PREFIX}
		-DCMAKE_PREFIX_PATH=${CMAKE_PREFIX_PATH}
		-DCMAKE_TRY_COMPILE_CONFIGURATION=${CMAKE_TRY_COMPILE_CONFIGURATION}
		-DLIBXML2_WITH_PYTHON=OFF
		-DLIBXML2_WITH_TESTS=OFF
	INSTALL_DIR ${CMAKE_INSTALL_PREFIX}
)

ExternalProject_Add_Step(
	libxml2 install-licenses
	DEPENDEES install
	COMMAND ${CMAKE_COMMAND} -E copy <SOURCE_DIR>/Copyright ${CMAKE_INSTALL_FULL_DATADIR}/licenses/libxml2/Copyright
)
