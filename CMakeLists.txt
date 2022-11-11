cmake_minimum_required(VERSION 3.5 FATAL_ERROR)
project(gio-mq LANGUAGES C CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_BUILD_TYPE Debug)
find_package(fmt)

include_directories(src/include)
#aux_source_directory(src/common COMMON_SRC)

add_executable(gio-mq src/main.cpp )

target_link_libraries(gio-mq
PRIVATE
  fmt::fmt
  )


  # tests
if(NOT without-test)
  include(GoogleTest)
  add_executable(FooTest )
  gtest_add_tests(TARGET      FooTest
                TEST_SUFFIX .noArgs
                TEST_LIST   noArgsTests)
endif()





