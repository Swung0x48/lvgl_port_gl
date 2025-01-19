cmake_minimum_required(VERSION 3.28)
project(lvgl_port_gl C)

set(CMAKE_C_STANDARD 99)

add_subdirectory(lvgl)

add_executable(lvgl_port_gl main.c
        porting/lv_port_disp.c
        porting/lv_port_fs.c
        porting/lv_port_indev.c)

find_package(glfw3 3.4.0 EXACT REQUIRED PATHS /opt/homebrew/Cellar/glfw/3.4/lib/cmake/glfw3)
find_package(OpenGL REQUIRED)

target_link_libraries(lvgl_port_gl PRIVATE lvgl)
#target_link_libraries(lvgl_port_gl PRIVATE glfw3)
target_link_libraries(lvgl_port_gl PRIVATE OpenGL::GL)

target_include_directories(lvgl_port_gl PRIVATE /opt/homebrew/Cellar/glfw/3.4/include)
target_link_libraries(lvgl_port_gl PRIVATE /opt/homebrew/Cellar/glfw/3.4/lib/libglfw.dylib)
