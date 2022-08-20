ExternalProject_Add(
	boost
	URL
		https://sourceforge.net/projects/boost/files/boost/1.80.0/boost_1_80_0.7z/download
		https://boostorg.jfrog.io/artifactory/main/release/1.80.0/source/boost_1_80_0.7z
	#URL ${CMAKE_CURRENT_SOURCE_DIR}/boost_1_80_0.7z
	URL_MD5 50034b565a679d8d971a72f1dec1b0e2
	CONFIGURE_COMMAND ""
	BUILD_COMMAND ""
	BUILD_IN_SOURCE 1
	INSTALL_COMMAND ${CMAKE_COMMAND} -E copy_directory <SOURCE_DIR>/boost ${CMAKE_INSTALL_FULL_INCLUDEDIR}/boost
)

ExternalProject_Add_Step(
	boost install-licenses
	DEPENDEES install
	COMMAND ${CMAKE_COMMAND} -E copy <SOURCE_DIR>/LICENSE_1_0.txt ${CMAKE_INSTALL_FULL_DATADIR}/licenses/boost/LICENSE_1_0.txt
)
