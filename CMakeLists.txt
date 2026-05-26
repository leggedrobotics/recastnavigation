cmake_minimum_required(VERSION 3.16)
project(recast_navigation)

find_package(catkin REQUIRED)

set(${PROJECT_NAME}_DIRS
  DebugUtils/Include/
  Detour/Include/
  DetourTileCache/Include/
  DetourCrowd/Include/
  Recast/Include/
)

catkin_package(
  INCLUDE_DIRS ${${PROJECT_NAME}_DIRS}
  LIBRARIES ${PROJECT_NAME}
)

file(GLOB ${PROJECT_NAME}_SRCS
  DebugUtils/Source/*.cpp
  Detour/Source/*.cpp
  DetourTileCache/Source/*.cpp
  DetourCrowd/Source/*.cpp
  Recast/Source/*.cpp
)

add_library(${PROJECT_NAME} 
  ${${PROJECT_NAME}_SRCS}
)

target_compile_features(${PROJECT_NAME} PUBLIC cxx_std_17)

target_include_directories(${PROJECT_NAME}
  PUBLIC
    ${${PROJECT_NAME}_DIRS}
)

install(DIRECTORY ${${PROJECT_NAME}_DIRS}
  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
)

install(TARGETS ${PROJECT_NAME}
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
