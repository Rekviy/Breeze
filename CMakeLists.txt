# application
cmake_minimum_required(VERSION 3.13)
set(APP_NAME Breeze)
project(${APP_NAME})

set_property(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT ${APP_NAME})
add_subdirectory(external)
list(APPEND CMAKE_MODULE_PATH "${OverTime_SOURCE_DIR}/cmake/Modules/")
include(OverTimeConfigDefine)

include(src/CMakeLists.txt)
list(APPEND GAME_SOURCE ${GAME_HEADER} ${GAME_RES})
add_executable(${APP_NAME} ${GAME_SOURCE})

target_link_libraries(${APP_NAME} PUBLIC external)

file(GLOB_RECURSE GAME_RES RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} CONFIGURE_DEPENDS 
"assets/**/*.png" "assets/**/*.frag" "assets/**/*.vert" 
)

foreach(item IN LISTS GAME_RES)
         res_mgmt(${APP_NAME} ${item})
endforeach()

target_compile_definitions(${APP_NAME} PRIVATE
    "$<$<CONFIG:Debug>:OT_DEBUG>"
)

target_include_directories(${APP_NAME} PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/src)

set_target_properties(${APP_NAME} PROPERTIES
                    RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/bin"
                    RESOURCE "${GAME_RES}" 
                    CMAKE_CONFIGURE_DEPENDS "${CMAKE_CURRENT_SOURCE_DIR}/assets"
                    )

if(WINDOWS)
target_compile_definitions(${APP_NAME} PRIVATE OT_PLATFORM_WINDOWS)
endif()
if(LINUX)
target_compile_definitions(${APP_NAME} PRIVATE OT_PLATFORM_LINUX)
endif()

set_property(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT ${APP_NAME})