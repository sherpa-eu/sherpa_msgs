cmake_minimum_required(VERSION 2.8.3)
project(sherpa_msgs)

set(MSG_DEPS
  std_msgs
  geometry_msgs
  actionlib_msgs
)

set(MSG_FILES
  Dummy.msg
  Battery.msg
  Beacon.msg
  LoggedBattery.msg
  LoggedBatteryList.msg
  LoggedRDFEntry.msg
)

set(SRV_FILES
  ReferenceDesignator.srv
)

set(ACT_FILES
  LogEvent.action
  Mount.action
  MoveTo.action
  SetAltitude.action
  TakePicture.action
  ToggleActuator.action
  ToggleVictimTracking.action
  PerformDesignator.action
)

find_package(catkin REQUIRED COMPONENTS
  ${MSG_DEPS}
  message_generation
  actionlib
)

add_message_files(DIRECTORY msg FILES ${MSG_FILES})
add_service_files(FILES ${SRV_FILES})
add_action_files(DIRECTORY action FILES ${ACT_FILES})

generate_messages(DEPENDENCIES ${MSG_DEPS})

catkin_package(CATKIN_DEPENDS ${MSG_DEPS} message_runtime actionlib)

