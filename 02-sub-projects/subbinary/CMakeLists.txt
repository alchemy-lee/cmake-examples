project(subbinary)

add_executable(${PROJECT_NAME} main.cpp)

target_link_libraries(${PROJECT_NAME}
    sublibrary1
    sublibrary2
)