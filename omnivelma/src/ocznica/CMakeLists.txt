cmake_minimum_required(VERSION 2.8.3)
project(ocznica)

find_package(catkin REQUIRED COMPONENTS
  gazebo_ros
  roscpp
  omnivelma_msgs
)

catkin_package(
	CATKIN_DEPENDS 
	omnivelma_msgs
	gazebo_ros
	roscpp 
)

find_package(gazebo REQUIRED)
find_package(roscpp REQUIRED)
find_package(omnivelma_msgs REQUIRED)

set(CMAKE_CXX_FLAGS   "-Wall -Wpedantic --std=c++14")
link_directories(${GAZEBO_LIBRARY_DIRS})
include_directories(${Boost_INCLUDE_DIR} ${catkin_INCLUDE_DIRS} ${GAZEBO_INCLUDE_DIRS})
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${GAZEBO_CXX_FLAGS}")

add_library(${PROJECT_NAME} src/ocznica.cpp)
add_dependencies(${PROJECT_NAME} ${catkin_EXPORTED_TARGETS})
target_link_libraries(${PROJECT_NAME} ${catkin_LIBRARIES} ${GAZEBO_LIBRARIES} ${roscpp_LIBRARIES})
