cmake_minimum_required(VERSION 3.18 FATAL_ERROR)
project(nvfuser)
find_package(Torch REQUIRED)
message(STATUS "torch libraries: ${TORCH_LIBRARIES}")

add_subdirectory(./googletest)

add_executable(testt ./main.cpp)
set_property(TARGET testt PROPERTY CXX_STANDARD 17)
target_link_libraries(testt PRIVATE gtest_main)
# commenting out ${TORCH_LIBRARIES} linking seems to get it to work
target_link_libraries(testt PRIVATE ${TORCH_LIBRARIES})
