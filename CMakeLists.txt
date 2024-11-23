cmake_minimum_required(VERSION 3.11)

project(seabattle CXX)
set(CMAKE_CXX_STANDARD 20)



# Платформы вроде linux требуют подключения библиотеки pthread для
# поддержки стандартных потоков.
# Следующие две строки подключат эту библиотеку на таких платформах
set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)

# Проект содержит единственный исходный файл src/main.cpp
add_executable(seabattle src/main.cpp)
# Просим компоновщик подключить библиотеку для поддержки потоков
target_link_libraries(seabattle PRIVATE Threads::Threads)

target_include_directories(seabattle PUBLIC 
  src/
  asio/asio/include/
)

add_compile_definitions(ASIO_STANDALONE)
# add_compile_definitions(BOOST_ASIO_HEADER_ONLY)
# add_compile_definitions(BOOST_ASIO_STANDALONE)
# add_compile_definitions(BOOST_ASIO_HAS_THREADS)
# add_subdirectory(asio)
# target_link_libraries(seabattle PUBLIC  asio)


#define ASIO_STANDALONE 
#define ASIO_HAS_STD_ADDRESSOF
#define ASIO_HAS_STD_ARRAY
#define ASIO_HAS_CSTDINT
#define ASIO_HAS_STD_SHARED_PTR
#define ASIO_HAS_STD_TYPE_TRAITS