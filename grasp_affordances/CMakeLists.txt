cmake_minimum_required(VERSION 2.8.3)
project(grasp_affordances)

add_definitions(-std=c++11)

find_package(catkin_simple REQUIRED)
catkin_simple(ALL_DEPS_REQUIRED)

cs_add_library(${PROJECT_NAME}_library
    src/grasp_affordances.cpp
    src/template_alignment.cpp
    src/featurecloud.cpp
)

cs_add_executable(${PROJECT_NAME}_node src/${PROJECT_NAME}_node.cpp )
target_link_libraries(${PROJECT_NAME}_node
  ${PROJECT_NAME}_library)

cs_install()
cs_export()
