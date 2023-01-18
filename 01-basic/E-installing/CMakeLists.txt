cmake_minimum_required(VERSION 3.5)

project(examples_install)

# Create a library
add_library(examples_library SHARED
    src/Hello.cpp
)

target_include_directories(examples_library
    PUBLIC
        ${PROJECT_SOURCE_DIR}/include
)

# Create an executable
add_executable(examples_bin
    src/main.cpp
)

target_link_libraries(examples_bin
    PRIVATE
        examples_library
)


# Install
install(TARGETS examples_bin
    DESTINATION bin)

install(TARGETS examples_library
    LIBRARY DESTINATION lib)

install(DIRECTORY ${PROJECT_SOURCE_DIR}/include
    DESTINATION include)

install(FILES cmake_examples.conf
    DESTINATION etc)


# 安装后在 build 目录下自动生成 install_manifest.txt 文件：
# /usr/local/bin/examples_bin
# /usr/local/lib/libexamples_library.dylib
# /usr/local/include/include/installing/Hello.h
# /usr/local/etc/cmake_examples.conf

# 安装的根目录由变量 CMAKE_INSTALL_PREFIX 指定，默认为 /usr/local