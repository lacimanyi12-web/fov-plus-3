cmake_minimum_required(VERSION 3.21)

include(${CMAKE_CURRENT_LIST_DIR}/qpm_defines.cmake)

project(${COMPILE_ID})

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED 20)

add_compile_options(-O3 -frtti -fexceptions -fvisibility=hidden)
add_compile_definitions(VERSION="${MOD_VERSION}")
add_compile_definitions(MOD_ID="${MOD_ID}")

file(GLOB_RECURSE SOURCE_FILES ${CMAKE_CURRENT_LIST_DIR}/src/*.cpp)
file(GLOB_RECURSE HEADER_FILES ${CMAKE_CURRENT_LIST_DIR}/include/*.hpp ${CMAKE_CURRENT_LIST_DIR}/include/*.h)

add_library(${COMPILE_ID} SHARED ${SOURCE_FILES} ${HEADER_FILES})

target_include_directories(${COMPILE_ID} PRIVATE ${CMAKE_CURRENT_LIST_DIR}/include)
target_include_directories(${COMPILE_ID} PRIVATE ${CMAKE_CURRENT_LIST_DIR}/shared)
target_include_directories(${COMPILE_ID} SYSTEM PRIVATE ${EXTERN_DIR}/includes)

target_link_libraries(${COMPILE_ID} PRIVATE -llog -landroid)

include(${CMAKE_CURRENT_LIST_DIR}/extern.cmake)
