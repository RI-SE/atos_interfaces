cmake_minimum_required(VERSION 3.5)
project(atos_interfaces)

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
find_package(builtin_interfaces REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(geographic_msgs REQUIRED)
find_package(std_msgs REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME}
  "msg/ISO22133/ActionConfiguration.msg"
  "msg/ISO22133/TriggerConfiguration.msg"
  "msg/ISO22133/TriggerEventOccurred.msg"
  "msg/ISO22133/ExecuteAction.msg"
  "msg/ISO22133/Monitor.msg"
  "msg/V2X/V2x.msg"
  "msg/V2X/V2xTriggerConfiguration.msg"
  "msg/ControlSignalPercentage.msg"
  "msg/ATOSHeader.msg" 
  "msg/ManoeuvreCommand.msg"
  "msg/ObjectEnabled.msg"
  "msg/ObjectId.msg"
  "msg/ObjectIdArray.msg"
  "msg/ObjectState.msg"
  "msg/ObjectDriveDirection.msg"
  "msg/ObjectErrorType.msg"
  "msg/ReadyToArm.msg"
  "msg/CartesianTrajectory.msg"
  "msg/CartesianTrajectoryPoint.msg"
  "msg/CartesianTolerance.msg"
  "msg/ObjectTriggerStart.msg"
  "srv/GetObjectIds.srv"
  "srv/GetTestOrigin.srv"
  "srv/GetObjectTriggerStart.srv"
  "srv/GetObjectTrajectory.srv"
  "srv/GetObjectIp.srv"
  DEPENDENCIES builtin_interfaces geometry_msgs geographic_msgs std_msgs
)

ament_package()
