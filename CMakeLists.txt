cmake_minimum_required(VERSION 3.5)
project(maestro_interfaces)

# Default to C99
if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(std_msgs REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME}
  "msg/Accm.msg"
  "msg/ControlSignalPercentage.msg"
  "msg/Exac.msg"
  "msg/MaestroHeader.msg" 
  "msg/ManoeuvreCommand.msg"
  "msg/Monitor.msg"
  "msg/ObjectEnabled.msg"
  "msg/ObjectId.msg"
  "msg/ObjectIdArray.msg"
  "msg/ObjectState.msg"
  "msg/Trajectory.msg"
  "msg/TrajectoryPoint.msg"
  "msg/TriggerEvent.msg"
  "srv/GetObjectIds.srv"
  DEPENDENCIES geometry_msgs std_msgs
)



ament_package()
