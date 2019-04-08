cmake_minimum_required(VERSION 2.8.3)
project(offb_enable)

## Compile as C++11, supported in ROS Kinetic and newer
add_compile_options(-std=c++11)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS
  geometry_msgs
  mavros
  roscpp
  rospy
  std_msgs
)

catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES offb_enable
#  CATKIN_DEPENDS geometry_msgs mavros roscpp rospy std_msgs
#  DEPENDS system_lib
)


include_directories(
# include
  ${catkin_INCLUDE_DIRS}
)
# for simulation, enable OFFBOARD automatic
add_executable(offb_enable_simulation src/offb_enable_simulation.cpp)
target_link_libraries(offb_enable_simulation ${catkin_LIBRARIES})

# for real fly, enable OFFBOARD by RC switch
add_executable(offb_enable src/offb_enable.cpp)
target_link_libraries(offb_enable ${catkin_LIBRARIES})