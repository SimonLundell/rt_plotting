cmake_minimum_required(VERSION 3.20)

project(rt_plot)

add_compile_options(-g -Wall -Wformat)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++17")

include_directories(
    ${CMAKE_CURRENT_SOURCE_DIR}/resources
    ${CMAKE_CURRENT_SOURCE_DIR}/resources/SDL2
    )

file(GLOB srcs src/*.cpp)
file(GLOB libs resources/*.cpp)

add_library(objs OBJECT ${libs})

add_executable(rt_plot ${srcs})

target_link_libraries(rt_plot PUBLIC objs)
target_link_libraries(rt_plot PUBLIC SDL2 SDL2_ttf)
target_link_libraries(rt_plot PUBLIC dl GL)

target_sources(
    rt_plot PRIVATE
    ${srcs}
)