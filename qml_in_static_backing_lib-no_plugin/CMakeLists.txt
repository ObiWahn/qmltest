cmake_minimum_required(VERSION 3.5)
project(application)

cmake_policy(SET CMP0071 NEW)
set(CMAKE_CXX_STANDARD 20 CACHE STRING "c++ version to use" FORCE)
set(CMAKE_CXX_EXTENSIONS ON CACHE BOOL "use gnu++" FORCE)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

add_executable(application application.cpp)
add_subdirectory(./ui)
target_link_libraries(application PUBLIC ui)
