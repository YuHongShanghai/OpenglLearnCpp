cmake_minimum_required(VERSION 3.27)
project(OpenglLearnCpp)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_C_STANDARD 11)

set(GLFW_DIR ${CMAKE_CURRENT_SOURCE_DIR}/glfw)
set(GLAD_DIR ${CMAKE_CURRENT_SOURCE_DIR}/glad)

set(SHADER_DIR "${CMAKE_SOURCE_DIR}/shaders")
add_compile_definitions(SHADER_DIR="${SHADER_DIR}")

set(RES_DIR "${CMAKE_SOURCE_DIR}/res")
add_compile_definitions(RES_DIR="${RES_DIR}")

file(GLOB src-files
        ${CMAKE_SOURCE_DIR}/*.cpp
        ${GLAD_DIR}/src/*.c)

add_executable(${PROJECT_NAME} ${src-files})

target_include_directories(${PROJECT_NAME}
        PRIVATE
        ${CMAKE_SOURCE_DIR}
        ${GLFW_DIR}/include
        ${GLAD_DIR}/include
)

target_link_libraries(${PROJECT_NAME}
        PRIVATE
        ${GLFW_DIR}/lib/libglfw3.a
        "-framework Cocoa"
        "-framework OpenGL"
        "-framework IOKit"
        "-framework CoreFoundation"
)