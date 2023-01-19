cmake_minimum_required(VERSION 3.5)

project(third_party)

# Boost - Name of the library. This is part of used to find the module file FindBoost.cmake
# 1.46.1 - The minimum version of boost to find
# REQUIRED - Tells the module that this is required and to fail if it cannot be found
# COMPONENTS - The list of components to find in the library.
find_package(Boost 1.46.1 REQUIRED COMPONENTS filesystem system)

# Boost_FOUND、Boost_INCLUDE_DIRS 等变量的描述位于 FindBoost.cmake 文件中
# macos 中使用 homebrew 安装 cmake，则 FindXXX.cmake 文件位于 /opt/homebrew/opt/cmake/share/cmake/Modules

if(Boost_FOUND)
    message("boost found: ${Boost_INCLUDE_DIRS}")
else()
    message(FATAL_ERROR "Cannot find Boost")
endif()


add_executable(third_party main.cpp)


# 现代 cmake librar 支持 Alias / Imported targets，可以使用 :: 进行链接
target_link_libraries(third_party
    PRIVATE
        Boost::filesystem
)

# 对于一些旧的库，可以使用下面方法链接
# # Include the boost headers
# target_include_directories( third_party
#     PRIVATE ${Boost_INCLUDE_DIRS}
# )

# # link against the boost libraries
# target_link_libraries( third_party
#     PRIVATE
#     ${Boost_SYSTEM_LIBRARY}
#     ${Boost_FILESYSTEM_LIBRARY}
# )

# Path used for searching by FIND_XXX()
message("system: ${CMAKE_SYSTEM_PREFIX_PATH}")