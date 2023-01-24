project(sublibrary2)


# header-only library
# An INTERFACE library target does not compile sources 
#   and does not produce a library artifact on disk
add_library(${PROJECT_NAME} INTERFACE)

target_include_directories(${PROJECT_NAME}
    INTERFACE
        ${PROJECT_SOURCE_DIR}/include
)