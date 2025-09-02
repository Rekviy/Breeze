cmake_minimum_required(VERSION 3.11)

include(FetchContent)

project(external)

add_library(${PROJECT_NAME} INTERFACE)

FetchContent_Declare(
  OverTime
  GIT_REPOSITORY https://github.com/Rekviy/OverTime.git
  GIT_TAG        v0.1
)

 set(FETCHCONTENT_BASE_DIR ${CMAKE_CURRENT_SOURCE_DIR})

FetchContent_MakeAvailable(OverTime)

target_link_libraries(${PROJECT_NAME} INTERFACE overtime)
