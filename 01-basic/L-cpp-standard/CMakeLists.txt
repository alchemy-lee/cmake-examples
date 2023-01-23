cmake_minimum_required(VERSION 3.8)

project(hello_cpp11)



# 指定 c++ 标准
set(CMAKE_CXX_STANDARD 11)

# New in version 3.8
# target_compile_features(hello_cpp11 PUBLIC c_std_11)


add_executable(hello_cpp11 main.cpp)