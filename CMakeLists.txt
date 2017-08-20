cmake_minimum_required(VERSION 3.9)
project(nginx)

set(CMAKE_C_STANDARD 99)

include_directories(src/core)
include_directories(src/event)
include_directories(src/event/modules)
include_directories(src/http)
include_directories(src/http/modules)
include_directories(src/os/unix)
include_directories(src/objs)

AUX_SOURCE_DIRECTORY(src/core SRC)
AUX_SOURCE_DIRECTORY(src/event SRC)
AUX_SOURCE_DIRECTORY(src/event/modules SRC)
AUX_SOURCE_DIRECTORY(src/http SRC)
AUX_SOURCE_DIRECTORY(src/http/modules SRC)
AUX_SOURCE_DIRECTORY(src/os/unix SRC)
AUX_SOURCE_DIRECTORY(src/objs SRC)



set(SOURCE_FILES ${SRC})
add_executable(nginx ${SOURCE_FILES})
target_link_libraries(nginx dl pthread crypt pcre z)