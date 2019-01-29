project(PARTICLE_FILTER)

cmake_minimum_required (VERSION 3.5)

add_definitions(-std=c++11)

set(CXX_FLAGS "-Wall")
set(CMAKE_CXX_FLAGS "${CXX_FLAGS}")

set(sources src/particle_filter.cpp src/main.cpp)

set(uWS_CUSTOM_INSTALL_DIR "YES")  # NO for system-wide install

if(${CMAKE_SYSTEM_NAME} MATCHES "Darwin") 

include_directories(/usr/local/include)
include_directories(/usr/local/opt/openssl/include)
link_directories(/usr/local/lib)
link_directories(/usr/local/opt/openssl/lib)
link_directories(/usr/local/Cellar/libuv/1*/lib)

endif(${CMAKE_SYSTEM_NAME} MATCHES "Darwin") 

#Minor addition for convenience
if(${uWS_CUSTOM_INSTALL_DIR} MATCHES "YES")
include_directories(../uWebSockets/bin/include)
link_directories(../uWebSockets/bin/lib64)
endif(${uWS_CUSTOM_INSTALL_DIR} MATCHES "YES")

add_executable(particle_filter ${sources})

target_link_libraries(particle_filter z ssl uv uWS)

