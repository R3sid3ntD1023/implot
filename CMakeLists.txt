cmake_minimum_required(VERSION 3.10)

find_package(imgui CONFIG REQUIRED)

option(IMPLOT_DEMO "Build impot_demo.cpp" ON)

set(IMPLOT_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/implot.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/implot_items.cpp
)

if(IMPLOT_DEMO)
  list(APPEND IMPLOT_SOURCES ${CMAKE_CURRENT_SOURCE_DIR}/implot_demo.cpp)
endif()

set(PROJECT_NAME implot)

add_library(${PROJECT_NAME} STATIC ${IMPLOT_SOURCES})
add_library(implot::implot ALIAS implot)
target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
target_link_libraries(${PROJECT_NAME} PUBLIC imgui)
target_compile_definitions(${PROJECT_NAME} PUBLIC _CRT_SECURE_NO_WARNINGS)

