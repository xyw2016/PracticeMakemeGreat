cmake_minimum_required(VERSION 3.5)


project(hello_cpp11)


include(CheckCXXCompilerFlag)
CHECK_CXX_COMPILER_FLAG("-std=c++11" COMPILER_SUPPORTS_CXX11) #check c++11
CHECK_CXX_COMPILER_FLAG("-std=c++0x" COMPILER_SUPPORTS_CXX0X) #check c++0x



if(COMPILER_SUPPORTS_CXX11)
    set(CMAKE_CXX_FLAGES "${CMAKE_CXX_FLAGS} -std=c++11")
    message("$-std=c++11")
elseif(COMPILER_SUPPORTS_CXX0X)
    set(CMAKE_CXX_FLASGS "${CMAKE_CXX_FLAGS} -std=c++0x")
    message("$-std=c++0x")
else()
    message(STATUS "The compiler ${CMAKE_CXX_COMPILER} has no C++11 support. Please use a different C++ compiler.")
endif()
# if compiler supports c++11 and c++0x both, it will compile by c++11 firstly.
# if compiler doesn't support c++11, it will compile by c++0x


add_executable(hello_cpp11 main.cpp)