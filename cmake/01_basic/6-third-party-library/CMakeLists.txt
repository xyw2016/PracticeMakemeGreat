
cmake_minimum_required(VERSION 3.5)




# Set the project name
project (third_party_include)
set(CMAKE_CXX_STANDARD 11)


# find a boost install with the libraries filesystem and system
find_package(Boost 1.50 REQUIRED COMPONENTS filesystem system)
include_directories(SYSTEM ${Boost_INCLUDE_DIRS})


# check if boost was found
if(Boost_FOUND)
    message ("boost found")
else()
    message (FATAL_ERROR "Cannot find Boost")
endif()

# Add an executable
add_executable(third_party_include main.cpp)

# link against the boost libraries
target_link_libraries( third_party_include ${Boost_LIBRARIES})
