ExternalProject_Add(
	boost
	URL
		https://sourceforge.net/projects/boost/files/boost/1.77.0/boost_1_77_0.7z/download
		https://boostorg.jfrog.io/artifactory/main/release/1.77.0/source/boost_1_77_0.7z
	#URL ${CMAKE_CURRENT_SOURCE_DIR}/boost_1_77_0.7z
	URL_MD5 74b23277a3bc1585e5ff8b0a633a2b97
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
