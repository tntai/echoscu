cmake_minimum_required(VERSION 2.8.12)
project(echoscu)

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

add_executable(echoscu echoscu.cc)
target_link_libraries(echoscu ${CONAN_LIBS})
