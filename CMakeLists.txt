cmake_minimum_required(VERSION 3.10)
project(dlib-tutorial)

add_definitions(-DPROJECT_SOURCE_ROOT="${PROJECT_SOURCE_DIR}")

include_directories(${PROJECT_SOURCE_DIR}/include/)
link_directories(${PROJECT_SOURCE_DIR}/library/)
link_libraries(dlib)

add_executable(face_recognize source/dnn_face_recognition_ex.cpp)
target_link_libraries(face_recognize dlib X11 pthread jpeg)