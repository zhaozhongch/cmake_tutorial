cmake_minimum_required(VERSION 2.6.0)

project(TestInstall)

# Add to module path, so we can find our cmake modules
list( APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake_modules)

include_directories( ${PROJECT_SOURCE_DIR}/include)

add_library(test_install STATIC src/test_install.cpp)

#The following will do install
include(install_package)
set(ICPCUDA_LIBRARIES icpcuda)
install_package(
  PKG_NAME TestInstall
  LIB_NAME test_install
  VERSION 0.2
  DESCRIPTION "installation test"
  INSTALL_INCLUDE_DIR true
  DESTINATION ${CMAKE_INSTALL_PREFIX}
  #INCLUDE_DIRS ${REQUIRED_INCLUDE_DIRS}
  #LINK_LIBS ${REQUIRED_LIBRARIES}
  )

#The following can make `sudo make uninstall` work
include(${CMAKE_MODULE_PATH}/cmake_uninstall.cmake.in)

add_custom_target(uninstall
    COMMAND ${CMAKE_COMMAND} -P ${CMAKE_CURRENT_BINARY_DIR}/cmake_uninstall.cmake)

