cmake_minimum_required(VERSION 3.20)

project(demo)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)


add_subdirectory(glfw-3.4)
add_executable(demo demo.cpp)
target_link_libraries(demo PRIVATE 
glfw 
${PROJECT_SOURCE_DIR}/libEGL.lib
${PROJECT_SOURCE_DIR}/libGLESv2.lib
${PROJECT_SOURCE_DIR}/impeller.dll.lib 
)

add_custom_command(TARGET demo POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_directory
        "${PROJECT_SOURCE_DIR}/dll"
        $<TARGET_FILE_DIR:demo>)