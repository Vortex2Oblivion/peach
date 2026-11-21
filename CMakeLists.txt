cmake_minimum_required(VERSION 4.1)
project(peach VERSION 0.0.1 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)

file(GLOB_RECURSE PEACH_SRC "peach/*.cpp")
add_library(peach STATIC ${PEACH_SRC})

target_include_directories(${PROJECT_NAME}
        PUBLIC
        $<INSTALL_INTERFACE:include>
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
        external/pugixml
        external/raylib
        PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}/src
)

target_link_libraries(${PROJECT_NAME} PUBLIC raylib pugixml)