cmake_minimum_required(VERSION 3.5)


project(hello_library)



if( CMAKE_INSTALL_PREFIX_INITIALIZED_TO_DEFAULT )
  message(STATUS "Setting default CMAKE_INSTALL_PREFIX path to ${CMAKE_BINARY_DIR}/install")
  set(CMAKE_INSTALL_PREFIX "${CMAKE_BINARY_DIR}/install" CACHE STRING "The path to use for make install" FORCE)
endif()


add_library(hello_library SHARED src/hello.cpp)


add_library(hello::library ALIAS hello_library) 
# alias name
target_include_directories(hello_library PUBLIC ${PROJECT_SOURCE_DIR}/inc)


add_executable(hello_binary src/main.cpp)
target_link_libraries(hello_binary PRIVATE hello::library)

install (TARGETS hello_binary DESTINATION bin)

install (TARGETS hello_library LIBRARY DESTINATION lib)

install (DIRECTORY ${PROJECT_SOURCE_DIR}/inc/ DESTINATION include)

install (FILES cmake-examples.conf DESTINATION etc)
