cmake_minimum_required(VERSION 3.5)
project(cpp_pubsub)

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)
# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

add_executable(DEC src/publisher_member_function.cpp)
ament_target_dependencies(DEC rclcpp std_msgs)

install(TARGETS
  DEC
  DESTINATION lib/${PROJECT_NAME})
  
add_executable(dnzngn src/subscriber_member_function.cpp)
ament_target_dependencies(dnzngn rclcpp std_msgs)

install(TARGETS
  DEC
  dnzngn
  DESTINATION lib/${PROJECT_NAME})
  
ament_package()
