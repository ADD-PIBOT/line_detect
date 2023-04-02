cmake_minimum_required(VERSION 3.0.2)
project(line_detect)

## Compile as C++11, supported in ROS Kinetic and newer
# add_compile_options(-std=c++11)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS
  cv_bridge
  roscpp
  sensor_msgs
  std_msgs
  aviation_master
  image_transport
  message_generation
  geometry_msgs
)

find_package(OpenCV REQUIRED)

catkin_package(
  # INCLUDE_DIRS include
  LIBRARIES opencv
  CATKIN_DEPENDS cv_bridge image_transport roscpp sensor_msgs std_msgs message_generation geometry_msgs aviation_master
)

###########
## Build ##
###########

## Specify additional locations of header files
## Your package locations should be listed before other locations
include_directories(
# include
  ${catkin_INCLUDE_DIRS}
  ${OpenCV_INCLUDE_DIRS}
)

add_executable(yellow_detect_node src/detect_yellow_node.cpp)
target_link_libraries(yellow_detect_node ${catkin_LIBRARIES} ${OpenCV_LIBRARIES})

add_executable(white_detect_node src/detect_white_node.cpp)
target_link_libraries(white_detect_node ${catkin_LIBRARIES} ${OpenCV_LIBRARIES})
