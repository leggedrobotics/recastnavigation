cmake_minimum_required(VERSION 3.1)
project(recast_navigation)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

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

include_directories(${${PROJECT_NAME}_DIRS})

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

# install(DIRECTORY ${${PROJECT_NAME}_DIRS}
#   DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
# )

# install(TARGETS ${PROJECT_NAME}
#   ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
#   LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
#   RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
# )
