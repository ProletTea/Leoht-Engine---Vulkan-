cmake_minimum_required(VERSION 3.16)
project(main CXX)
set(CMAKE_CXX_STANDARD 23)

# include_dictiories (

# )

aux_source_directory(${PROJECT_SOURCE_DIR}/engine/src SRC_LIST)
add_executable(Leoht ${SRC_LIST})


set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_CURRENT_SOURCE_DIR}/cmake)
set(glm_DIR D:/libraries/glm-1.0.3/glm-installed/share/glm)

find_package(Vulkan REQUIRED)
find_package(GLFW3 3.5 REQUIRED)
# find_package(GLM REQUIRED)
find_package(glm CONFIG REQUIRED
    PATHS "D:/libraries/glm-1.0.3/share/glm"
    NO_DEFAULT_PATH
)

# find_package (Eigen3 REQUIRED NO_MODULE)

target_include_directories(Leoht PRIVATE ${GLFW3_INCLUDE_DIR})
target_include_directories(Leoht PRIVATE ${Vulkan_INCLUDE_DIRS})
# target_include_directories(Leoht PRIVATE glm::glm)
target_link_libraries(Leoht ${GLFW3_LIBRARY})
target_link_libraries(Leoht ${Vulkan_LIBRARIES})
target_link_libraries(Leoht glm::glm)

# message(${GLM_INCLUDE_DIR})
if(TARGET glm::glm)
    message(STATUS "GLM target found")
else()
    message(FATAL_ERROR "GLM target not found")
endif()

# target_link_libraries (example Eigen3::Eigen)
