cmake_minimum_required(VERSION 3.1)
project(echoscu)

# set the C++ standard to C++ 11
set(CMAKE_CXX_STANDARD 11)

# From CMAKE-CONAN
list(APPEND CMAKE_MODULE_PATH ${CMAKE_BINARY_DIR})
list(APPEND CMAKE_PREFIX_PATH ${CMAKE_BINARY_DIR})

if(NOT EXISTS "${CMAKE_BINARY_DIR}/conan.cmake")
  message(STATUS "Downloading conan.cmake from https://github.com/conan-io/cmake-conan")
  file(DOWNLOAD "https://raw.githubusercontent.com/conan-io/cmake-conan/v0.16.1/conan.cmake"
                "${CMAKE_BINARY_DIR}/conan.cmake"
                EXPECTED_HASH SHA256=396e16d0f5eabdc6a14afddbcfff62a54a7ee75c6da23f32f7a31bc85db23484
                TLS_VERIFY ON)
endif()

include(${CMAKE_BINARY_DIR}/conan.cmake)

conan_cmake_configure(REQUIRES dcmtk/3.6.6
                      OPTIONS  dcmtk:with_openssl=False
                      GENERATORS cmake_find_package)

conan_cmake_autodetect(settings)

conan_cmake_install(PATH_OR_REFERENCE .
                    BUILD missing
                    REMOTE conan-center
                    SETTINGS ${settings})

find_package(dcmtk)

add_executable(${PROJECT_NAME} echoscu.cc)
target_link_libraries(${PROJECT_NAME} DCMTK::dcmpstat DCMTK::dcmnet DCMTK::dcmfg DCMTK::dcmdata DCMTK::oflog DCMTK::ofstd)
