cmake_minimum_required(VERSION 2.8.3)
project(omni_common)

find_package(catkin REQUIRED COMPONENTS 
  geometry_msgs 
  omni_msgs 
  sensor_msgs 
  std_msgs 
  tf
)

catkin_package(
CATKIN_DEPENDS 
  geometry_msgs 
  omni_description 
  omni_msgs 
  robot_state_publisher 
  sensor_msgs 
  std_msgs 
  tf
  xacro
)

set(OPENHAPTICS_INCLUDE_DIR C:/OpenHaptics/Developer/3.5.0/include C:/OpenHaptics/Developer/3.5.0/utilities/include)
set(PTHREADS_INCLUDE_DIR C:/pthreads) 
set(OPENHAPTICS_LINK_DIR  C:/OpenHaptics/Developer/3.5.0/lib/x64/Release C:/OpenHaptics/Developer/3.5.0/utilities/lib/x64/Release)
set(PTHREADS_LINK_DIR C:/pthreads) 



include_directories(${Boost_INCLUDE_DIR} ${catkin_INCLUDE_DIRS} ${OPENHAPTICS_INCLUDE_DIR} ${PTHREADS_INCLUDE_DIR})
link_directories(${OPENHAPTICS_LINK_DIR} ${PTHREADS_LINK_DIR})

#find_path(OPENHAPTICS_INCLUDE_DIR NAMES HD/hd.h HL/hl.h HDU/hdu.h PATHS C:/OpenHaptics/Developer/3.5.0 C:/OpenHaptics/Developer/3.5.0/utilities)
message(STATUS "${OPENHAPTICS_INCLUDE_DIR}")
if(NOT OPENHAPTICS_INCLUDE_DIR)
  set(OPENHAPTICS_MESSAGE "OPENHAPTICS was not found. If you do not have it you will not be able to use the Phantom Omni.")
  message(STATUS "${OPENHAPTICS_MESSAGE}") 
  return()
endif(NOT OPENHAPTICS_INCLUDE_DIR)
  
add_executable(omni src/omni.cpp)
target_link_libraries(omni HD HDU pthreadVCE3 ${catkin_LIBRARIES})
add_dependencies(omni omni_msgs_gencpp)

add_executable(omni_state src/omni_state.cpp)
target_link_libraries(omni_state HD HDU pthreadVCE3 ${catkin_LIBRARIES})
add_dependencies(omni_state omni_msgs_gencpp)

