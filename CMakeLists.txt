cmake_minimum_required(VERSION 3.18)
project(inih LANGUAGES C CXX VERSION 1.0)

add_library(${PROJECT_NAME} SHARED
    ini.c
    cpp/INIReader.cpp
)

# Mark INIReader.cpp as C++ (so it’s not compiled with nvcc)
set_source_files_properties(cpp/INIReader.cpp PROPERTIES LANGUAGE CXX)

# Export both include paths (cpp/ has INIReader.h, root has ini.h)
target_include_directories(${PROJECT_NAME} INTERFACE
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}/cpp
)