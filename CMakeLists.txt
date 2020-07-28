cmake_minimum_required(VERSION 3.10)
project(dlib-tutorial)

add_definitions(-DPROJECT_SOURCE_ROOT="${PROJECT_SOURCE_DIR}")

include_directories(${PROJECT_SOURCE_DIR}/include/)
link_directories(${PROJECT_SOURCE_DIR}/library/)
link_directories(${PROJECT_SOURCE_DIR}/library/3rdparty)
link_libraries(dlib)

set(opencv_3rdparty
        IlmImf
        ittnotify
        libjpeg-turbo
        libpng
        libtiff
        libwebp
        libjasper
        z
        )

set(opencv_gtk
        gio-2.0
        gthread-2.0
        gobject-2.0
        gmodule-2.0
        glib-2.0
        cairo
        gdk_pixbuf-2.0
        gdk-x11-2.0
        gtk-x11-2.0
        )

set(opencv_lib
        opencv_videoio
        opencv_imgproc
        opencv_imgcodecs
        opencv_highgui
        opencv_objdetect
        opencv_core
        )

add_executable(face_recognize source/dnn_face_recognition_ex.cpp)
target_link_libraries(face_recognize dlib X11 pthread jpeg)

add_executable(video_capture source/video_capture.cpp)
target_link_libraries(video_capture ${opencv_lib} ${opencv_3rdparty} ${opencv_gtk} pthread dl)

add_executable(face_detect source/face_detect.cpp)
target_link_libraries(face_detect ${opencv_lib} ${opencv_3rdparty} ${opencv_gtk} pthread dl)