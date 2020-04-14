cmake_minimum_required(VERSION 3.4.1)

#头文件
set(include_dir ${CMAKE_SOURCE_DIR}/giflib)
include_directories(${include_dir})

add_library(giflib STATIC giflib/egif_lib.c giflib/dgif_lib.c giflib/gif_font.c
        giflib/gif_err.c giflib/gifalloc.c giflib/openbsd-reallocarray.c)

#bitmap的包
find_library(graphics jnigraphics)

add_library(cyxGiflib SHARED CyxGifLib.cpp)

#目标库链接其他库
target_link_libraries(cyxGiflib giflib ${graphics})