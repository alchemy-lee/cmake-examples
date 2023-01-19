cmake_minimum_required(VERSION 3.5)

# CMAKE_C_FLAGS and CMAKE_CXX_FLAGS will set a compiler flag / definition globally for all targets in this directory or any included sub-directories. It is not recommended
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -DEX2")

project(compile_flags)

add_executable(compile_flags main.cpp)

# The recommended way to set C++ flags in modern CMake is to use per-target flags
# If the target was a library and the scope PUBLIC or INTERFACE has been chosen the definition would also be included in any executables that link this target.
target_compile_definitions(compile_flags
    PRIVATE EX3
)