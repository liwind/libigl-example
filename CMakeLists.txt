cmake_minimum_required(VERSION 3.20)
project(example)

set(LIBIGLDIR $ENV{LIBIGL_DIR} CACHE PATH "libigl path")
set(EIGEN3DIR $ENV{EIGEN3_ROOT} CACHE PATH "eigen3 path")
set(GLFWDIR ${CMAKE_SOURCE_DIR}/deps/glfw CACHE PATH "glfw path")
set(GLADDIR ${CMAKE_SOURCE_DIR}/deps/glad CACHE PATH "glad path")
include(FetchContent)
FetchContent_Declare(glad SOURCE_DIR ${GLADDIR})
FetchContent_Declare(glfw SOURCE_DIR ${GLFWDIR})
FetchContent_Declare(eigen SOURCE_DIR ${EIGEN3DIR})
FetchContent_Declare(libigl SOURCE_DIR ${LIBIGLDIR})
FetchContent_MakeAvailable(libigl)

# Libigl
# list(PREPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)
# include(libigl)

# Enable the target igl::glfw
igl_include(glfw)
#igl_include(imgui)
#igl_include(opengl)

# Add your project files and Link igl (and the glfw module) to your project
add_executable(10hello src/10hello.cpp)
target_link_libraries(10hello PUBLIC igl::glfw)
add_executable(11fileio src/11fileio.cpp)
target_link_libraries(11fileio PUBLIC igl::glfw)
