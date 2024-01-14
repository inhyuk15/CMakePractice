cmake_minimum_required(VERSION 3.15)

project(boost_chat_server)

set(CMAKE_CXX_STANDARD 20)

# set(BOOST_ROOT "/usr/local/Cellar/boost/1.82.0_1")
find_package(Boost 1.82.0 REQUIRED COMPONENTS system)
find_package(Protobuf REQUIRED)

file(GLOB SOURCE
    "${CMAKE_CURRENT_SOURCE_DIR}/ChatServer/*.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/ChatServer/*.cc"
    "${CMAKE_CURRENT_SOURCE_DIR}/ChatServer/Logger/*.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/ChatServer/Communicator/*.cpp"
)


add_executable(MyServer ${SOURCE})

target_include_directories(MyServer PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}/ChatServer
    ${CMAKE_CURRENT_SOURCE_DIR}/ChatServer/Logger
    ${CMAKE_CURRENT_SOURCE_DIR}/ChatServer/Logger/Observers
    ${CMAKE_CURRENT_SOURCE_DIR}/ChatServer/Communicator
)



# include_directories(${Boost_INCLUDE_DIR})
# link_libraries(${Boost_LIBRARIES})
target_include_directories(MyServer PRIVATE ${Boost_INCLUDE_DIR})
target_link_libraries(MyServer PRIVATE ${Boost_LIBRARIES})

target_include_directories(MyServer PRIVATE ${Protobuf_INCLUDE_DIR})
target_link_libraries(MyServer PRIVATE ${Protobuf_LIBRARIES})