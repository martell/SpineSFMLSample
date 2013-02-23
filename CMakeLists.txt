cmake_minimum_required(VERSION 2.8.8)

project(test)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)
include_directories(spine-runtimes/spine-cpp/includes)
include_directories(SFML/include)
					
link_directories(${CMAKE_CURRENT_SOURCE_DIR}/lib)
link_directories(SFML/lib) # SFML lib directory

#set(CMAKE_C_FLAGS ${CMAKE_C_FLAGS} "-std=gnu99")
set(CMAKE_CXX_FLAGS ${CMAKE_CXX_FLAGS} "-Wall")#-std=c++11 -U__STRICT_ANSI__")

FILE(GLOB SRCS
	RELATIVE ${CMAKE_CURRENT_SOURCE_DIR}
	${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp
	spine-runtimes/spine-cpp/src/json/*.cpp
	spine-runtimes/spine-cpp/src/spine/*.cpp
	spine-runtimes/spine-cpp/src/spine-sfml/*.cpp
)

add_executable(test WIN32 ${SRCS})
target_link_libraries(test sfml-main sfml-window sfml-graphics sfml-system)