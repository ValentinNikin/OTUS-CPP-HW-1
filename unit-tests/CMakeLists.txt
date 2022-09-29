
set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)

find_package(GTest REQUIRED)

set(UNIT_TEST_EXECUTABLE_NAME helloworld_unit_tests)

add_executable(
    ${UNIT_TEST_EXECUTABLE_NAME}
    main.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/lib-unittest.cpp)

message("${PROJECT_SOURCE_DIR}")

target_include_directories(
    ${UNIT_TEST_EXECUTABLE_NAME} 
    PRIVATE
    ${PROJECT_SOURCE_DIR}/lib/
    ${GTEST_INCLUDE_DIRS})

message("${GTEST_BOTH_LIBRARIES}")

target_link_libraries(
    ${UNIT_TEST_EXECUTABLE_NAME} 
    PRIVATE
    ${OTUS_CPP_HW_1_LIBRARY_NAME}
    ${GTEST_BOTH_LIBRARIES}
    ${CMAKE_THREAD_LIBS_INIT})

add_test(
    NAME test-all
    COMMAND ${UNIT_TEST_EXECUTABLE_NAME}
)