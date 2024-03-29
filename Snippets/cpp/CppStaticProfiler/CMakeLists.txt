cmake_minimum_required(VERSION 3.16)
project(example)

find_package(glog REQUIRED)

add_executable(${PROJECT_NAME} main.cpp Profiler.cpp)

target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_HOME_DIRECTORY})

target_link_libraries (${PROJECT_NAME} glog::glog)

target_compile_features(${PROJECT_NAME} PUBLIC cxx_std_17) # cxx_std_14 is minimum because of other dependencies

target_compile_options(${PROJECT_NAME} PUBLIC
  -Wall # It turns on (almost) all the warnings that g++ can tell you about.
        # If you're a beginner, it's good idea to compile with '-Wall'
        # because understanding and fixing those warnings can help you fix lots of different kinds of problems in your code.

  -Werror # If -Werror option is used, all warnings are recognized as errors. This flag is used when compiling more strictly.

  # -pthread # When you wanna link <thread> related libraries
)

set_target_properties(${PROJECT_NAME} PROPERTIES
  RUNTIME_OUTPUT_DIRECTORY "${CMAKE_HOME_DIRECTORY}/bin")
