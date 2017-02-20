cmake_minimum_required(VERSION 2.8.3)
project(icr)

add_definitions(-std=c++11)

find_package(catkin_simple REQUIRED)
catkin_simple(ALL_DEPS_REQUIRED)

cs_add_executable(icr_server src/icr_server.cpp src/icr_server_node.cpp)
cs_add_executable(model_server src/model_server.cpp src/model_server_node.cpp src/pose_broadcaster.cpp)
cs_add_executable(grasp_server src/grasp_server.cpp src/grasp_server_node.cpp src/phalange.cpp)

cs_install()
cs_export()
