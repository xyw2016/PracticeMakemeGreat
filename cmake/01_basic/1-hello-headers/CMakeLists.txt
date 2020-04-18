

cmake_minimum_required(VERSION 3.5)


project (hello_headers)


set (SOURCE 
     src/hello.cpp
     src/main.cpp)


add_executable(${PROJECT_NAME} ${SOURCE})


target_include_directories(hello_headers
	PRIVATE ${PROJECT_SOURCE_DIR}/inc)
