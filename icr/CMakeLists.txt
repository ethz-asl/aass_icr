cmake_minimum_required(VERSION 2.8.3)
project(icr)

add_definitions(-std=c++11)

find_package(catkin_simple REQUIRED)
catkin_simple(ALL_DEPS_REQUIRED)

### ---[ Find universal dependencies
set(CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake/Modules/" ${CMAKE_MODULE_PATH})

# TODO(gocarlos): Eventually its a good idea to add Qhull to
# this repository or to make a catkin qhull package

# Qhull
option(WITH_QHULL "Include convex-hull operations" TRUE)
if(WITH_QHULL)
  find_package(Qhull REQUIRED)
  if(QHULL_FOUND)
    include_directories(${QHULL_INCLUDE_DIRS})
  endif(QHULL_FOUND)
endif(WITH_QHULL)

cs_add_executable(icr_server src/icr_server.cpp src/icr_server_node.cpp)
cs_add_executable(model_server src/model_server.cpp src/model_server_node.cpp src/pose_broadcaster.cpp)
cs_add_executable(grasp_server src/grasp_server.cpp src/grasp_server_node.cpp src/phalange.cpp)

cs_install()
cs_export()
