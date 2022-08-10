cmake_minimum_required(VERSION 3.24.0)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/_out/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/_out/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/_out/bin)

project(LeagueBot)

add_subdirectory(_vendor/c_base)

file(GLOB_RECURSE SRC_FILES src/*.c)
add_executable(${PROJECT_NAME} ${SRC_FILES})

target_include_directories(${PROJECT_NAME}
	PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/src
	PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/_vendor/c_base/include)
target_link_libraries(${PROJECT_NAME} c_log c_core c_file)
