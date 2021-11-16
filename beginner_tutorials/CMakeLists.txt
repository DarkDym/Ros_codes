cmake_minimum_required(VERSION 3.0.2)
project(beginner_tutorials)
include($ENV{ROS_ROOT}/core/rosbuild/rosbuild.cmake)

find_package(catkin REQUIRED COMPONENTS
	roscpp
	rospy
	std_msgs
	geometry_msgs
  	sensor_msgs
  	tf
  	tf2_sensor_msgs
	gazebo_msgs
)

catkin_package(
	CATKIN_DEPENDS roscpp rospy std_msgs geometry_msgs message_runtime sensor_msgs tf2_sensor_msgs gazebo_msgs
	DEPENDS system_lib 
)

include_directories(
 include
 ${catkin_INCLUDE_DIRS}
)

## Build talker and listener
include_directories(include ${catkin_INCLUDE_DIRS})

add_executable(talker src/talker.cpp)
target_link_libraries(talker ${catkin_LIBRARIES})
#add_dependencies(talker beginner_tutorials_generate_messages_cpp)

add_executable(listener src/listener.cpp)
target_link_libraries(listener ${catkin_LIBRARIES})
#add_dependencies(listener beginner_tutorials_generate_messages_cpp)

## Build teste
add_executable(teste src/teste.cpp)
target_link_libraries(teste ${catkin_LIBRARIES})

# add_executable(get_gazebo src/get_gazebo_state.cpp)
# target_link_libraries(get_gazebo ${catkin_LIBRARIES})

## Build Sockets
add_executable(socket_server src/socket_server.cpp)
target_link_libraries(socket_server ${catkin_LIBRARIES})
add_executable(socket_client src/socket_client.cpp)
target_link_libraries(socket_client ${catkin_LIBRARIES})
add_executable(get_gazebo src/get_gazebo_state.cpp)
target_link_libraries(get_gazebo ${catkin_LIBRARIES})
