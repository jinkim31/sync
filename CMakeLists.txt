cmake_minimum_required(VERSION 3.24)
project(sync)
set(CMAKE_CXX_STANDARD 20)

add_subdirectory(lib/json)
include_directories(lib/json/include)

add_library(sync STATIC src/sync.cpp)
target_include_directories(sync PUBLIC src lib/json/include)

add_executable(test test/main.cpp)
target_link_libraries(test PRIVATE sync)

add_executable(test_polymorphic_vector test/polymorphic_vector.cpp)
target_link_libraries(test_polymorphic_vector PRIVATE sync)

add_executable(test_polymorphic_map test/polymorphic_map.cpp)
target_link_libraries(test_polymorphic_map PRIVATE sync)