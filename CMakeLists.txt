cmake_minimum_required(VERSION "3.18.3")
set(CMAKE_CXX_STANDARD 20)
project(ptest)

add_subdirectory(spdlog)

add_executable(Fserver buildConnection/main.cxx)
add_executable(Fclient buildConnection/client.cxx)

include_directories("./spdlog/include")

target_link_libraries(Fserver PUBLIC  spdlog pthread numa ibverbs rdmacm)
target_link_libraries(Fclient PUBLIC spdlog pthread numa ibverbs rdmacm)
#install(FILES "main.cpp" DESTINATION src)
