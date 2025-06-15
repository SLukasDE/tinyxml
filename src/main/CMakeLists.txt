include(FetchContent)

file(GLOB_RECURSE ${PROJECT_NAME}_SRC ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp)

if (BUILD_SHARED_LIBS)
    message(STATUS "-> lib type is SHARED")
    add_library(${PROJECT_NAME} SHARED ${${PROJECT_NAME}_SRC})
else (BUILD_SHARED_LIBS)
    message(STATUS "-> lib type is STATIC")
    add_library(${PROJECT_NAME} STATIC ${${PROJECT_NAME}_SRC})
endif (BUILD_SHARED_LIBS)

add_library(${PROJECT_NAME}::${PROJECT_NAME} ALIAS ${PROJECT_NAME})

target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

#target_link_libraries(${PROJECT_NAME} PUBLIC
#    rapidjson::rapidjson)
