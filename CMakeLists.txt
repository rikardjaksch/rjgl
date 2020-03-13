cmake_minimum_required(VERSION 3.10.0)
project(rjgl)


# Configure how we want to build GLFW
set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)

# Add all thirdparty libaries
add_subdirectory(thirdparty/glfw-3.3.2)
add_subdirectory(thirdparty/glad)

# Create a target for our runtime executable
add_executable(rjgl runtime/main.cpp)
set_property(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT rjgl)

# Link our executable to all libraries
target_link_libraries(rjgl glfw glad opengl32)