cmake_minimum_required(VERSION 3.16)
project(main CXX)
set(CMAKE_CXX_STANDARD 23)

# include_dictiories (

# )

aux_source_directory(${PROJECT_SOURCE_DIR}/engine/src SRC_LIST)
add_executable(Leoht ${SRC_LIST})


set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_CURRENT_SOURCE_DIR}/cmake)
find_package(Vulkan REQUIRED)
find_package(GLFW3 3.5 REQUIRED)
# find_package (Eigen3 REQUIRED NO_MODULE)

target_include_directories(Leoht PRIVATE "${GLFW3_INCLUDE_DIR}")
target_link_libraries(Leoht ${GLFW3_LIBRARY})
target_include_directories(Leoht PRIVATE ${Vulkan_INCLUDE_DIRS})
target_link_libraries(Leoht ${Vulkan_LIBRARIES})
# target_link_libraries (example Eigen3::Eigen)
