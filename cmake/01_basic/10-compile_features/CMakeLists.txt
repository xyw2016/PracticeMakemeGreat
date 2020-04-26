cmake_minimum_required(VERSION 3.5)


project(hello_cpp11)


add_executable(hello_cpp11 main.cpp)

target_compile_features(hello_cpp11 PUBLIC cxx_auto_type)
#set the c++ standard to the appropriate standard for using auto



message("List of compile features: ${CMAKE_CXX_COMPILE_FEATURES}")


