cmake_minimum_required(VERSION 3.14)

project(minidbg)
set(CMAKE_CXX_IMPLICIT_LINK_DIRECTORIES /usr/local/lib ${CMAKE_CXX_IMPLICIT_LINK_DIRECTORIES})

add_executable(${CMAKE_PROJECT_NAME}
  main.cpp
)

target_include_directories(${CMAKE_PROJECT_NAME} PRIVATE "/usr/local/include/libelfin/dwarf")
target_include_directories(${CMAKE_PROJECT_NAME} PRIVATE "/usr/local/include/libelfin/elf")

find_library(dwarf NAMES dwarf++)
find_library(elf NAMES elf++)

message(STATUS "${dwarf}")
message(STATUS "${elf}")

target_link_libraries(${CMAKE_PROJECT_NAME} PRIVATE "${elf}" "${dwarf}")
