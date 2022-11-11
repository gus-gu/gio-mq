include(GoogleTest)
# configure build of googletest
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
set(BUILD_GMOCK OFF CACHE BOOL "" FORCE)


add_executable(
    gio-mq-unitt-tests
    example_add.cpp
    example_subtract.cpp
    )

target_link_libraries(unit_tests
  PRIVATE
    example
    gtest_main
  )

# automatic discovery of unit tests

gtest_discover_tests(gio-mq-unitt-tests
  PROPERTIES
    LABELS "unit"
  DISCOVERY_TIMEOUT  # how long to wait (in seconds) before crashing
    240
  )