
cmake_minimum_required(VERSION 3.8)

file(GLOB IMPLOT_SRC CMAKE_CONFIGURE_DEPENDS *.h *.cpp)

add_library(ImPlot STATIC ${IMPLOT_SRC})
target_include_directories(ImPlot PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
find_package(imgui)
target_link_libraries(ImPlot PUBLIC imgui::imgui)

