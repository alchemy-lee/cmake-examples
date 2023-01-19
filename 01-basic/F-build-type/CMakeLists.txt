cmake_minimum_required(VERSION 3.5)

# CMAKE_BUILD_TYPE： 设置编译级别
# Release        - Adds the -O3 -DNDEBUG flags to the compiler
# Debug          - Adds the -g flag
# MinSizeRel     - Adds -Os -DNDEBUG
# RelWithDebInfo - Adds -O2 -g -DNDEBUG flags

# set 设置的变量只在当前脚本生效
# CACHE： 将变量持久化在缓存文件（CMakeCache.txt）中，每一次编译都会用到
# FORCE： 强制覆盖 CACHE 中的值
set(CMAKE_BUILD_TYPE Release CACHE STRING "The type of build" FORCE)

project(build_type)

add_executable(build_type main.cpp)