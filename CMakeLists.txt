cmake_minimum_required(VERSION 3.6)

project(wfrest_usage 
	LANGUAGES C CXX)


set(CXX_FLAGS
        -g
        -std=c++11
        -rdynamic
        -pthread
        -fno-exceptions
        )

find_package(ZLIB REQUIRED)
find_package(OpenSSL REQUIRED)
find_package(wfrest REQUIRED)

if(NOT wfrest_FOUND)
    message(FATAL_ERROR "can't find wfrest, please build it first")
endif()

add_executable(test test.cc)
target_link_libraries(test wfrest)
