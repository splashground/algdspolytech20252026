cmake_minimum_required(VERSION 3.10)
project(PriorityQueue)

# Настройка C стандарта
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# Поиск GoogleTest
find_package(GTest REQUIRED)

# Библиотека очереди
add_library(queue_lib src/queue.c)
target_include_directories(queue_lib PUBLIC include)

# Тесты
add_executable(queue_tests test/Test.cpp)
target_link_libraries(queue_tests queue_lib GTest::GTest GTest::Main)

# Включение тестов
include(GoogleTest)
gtest_discover_tests(queue_tests)
