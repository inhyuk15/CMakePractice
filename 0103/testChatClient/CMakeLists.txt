cmake_minimum_required(VERSION 3.15)

project(boost_chat_client)

set(CMAKE_CXX_STANDARD 20)

set(BOOST_ROOT "/usr/local/Cellar/boost/1.82.0_1")
find_package(Boost 1.82.0 REQUIRED COMPONENTS system)

file(GLOB SOURCE "main.cpp")

add_executable(MyClient ${SOURCE})

include_directories(${Boost_INCLUDE_DIR})

target_link_libraries(MyClient ${Boost_LIBRARIES})