# This Source Code Form is subject to the terms of the Mozilla Public
# License, v. 2.0. If a copy of the MPL was not distributed with this
# file, You can obtain one at https://mozilla.org/MPL/2.0/.

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
  "msg/ActionConfiguration.msg"
  "msg/TriggerConfiguration.msg"
  "msg/TriggerEventOccurred.msg"
  "msg/ExecuteAction.msg"
  "msg/Monitor.msg"
  "msg/V2x.msg"
  "msg/V2xTriggerConfiguration.msg"
  "msg/ControlSignalPercentage.msg"
  "msg/ATOSHeader.msg" 
  "msg/ManoeuvreCommand.msg"
  "msg/ObjectEnabled.msg"
  "msg/ObjectId.msg"
  "msg/ObjectIdArray.msg"
  "msg/ObjectState.msg"
  "msg/ObjectStateChange.msg"
  "msg/ObjectDriveDirection.msg"
  "msg/ObjectErrorType.msg"
  "msg/ReadyToArm.msg"
  "msg/CartesianTrajectory.msg"
  "msg/CartesianTrajectoryPoint.msg"
  "msg/CartesianTolerance.msg"
  "msg/ObjectTriggerStart.msg"
  "msg/StateChange.msg"
  "srv/GetObjectIds.srv"
  "srv/GetTestOrigin.srv"
  "srv/GetObjectTriggerStart.srv"
  "srv/GetObjectTrajectory.srv"
  "srv/GetObjectIp.srv"
  "srv/GetObjectControlState.srv"
  "srv/GetObjectReturnTrajectory.srv"
  "srv/SetObjectIp.srv"
  DEPENDENCIES builtin_interfaces geometry_msgs geographic_msgs std_msgs
)

ament_package()
