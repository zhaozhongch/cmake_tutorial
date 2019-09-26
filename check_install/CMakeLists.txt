cmake_minimum_required(VERSION 2.6.0)

project(CheckInstall)

# Add to module path, so we can find our cmake modules
#list( APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake_modules)

find_package(TestInstall REQUIRED)
#find_package(TestInstall2 REQUIRED)

add_executable(check_install_1 check_install_1.cpp)
target_link_libraries(check_install_1 ${TestInstall_LIBRARIES})

#add_executable(check_install_2 check_install_2.cpp)
#target_link_libraries(check_install_2 ${TestInstall2_LIBRARIES} ${TestInstall_LIBRARIES})


