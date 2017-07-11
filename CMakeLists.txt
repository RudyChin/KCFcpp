cmake_minimum_required(VERSION 2.8)
project(kcf)

find_package(OpenCV REQUIRED)

if(NOT WIN32)
ADD_DEFINITIONS("-std=c++0x -O3")
endif(NOT WIN32)

include_directories(src) 
FILE(GLOB_RECURSE headers "src/*.hpp" "src/*.h")
FILE(GLOB_RECURSE sourcefiles "src/*.cpp")
add_library(KCF SHARED ${sourcefiles})
target_link_libraries( KCF ${OpenCV_LIBS})
install(TARGETS KCF LIBRARY DESTINATION lib)
install(FILES ${headers} DESTINATION include)




