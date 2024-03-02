cmake_minimum_required(VERSION 3.10)

project(HelloWorld)

find_package(SDL2 CONFIG REQUIRED)
find_package(SDL2_ttf)
find_package(imgui CONFIG REQUIRED COMPONENTS sdl2 sdl2-renderer)

add_executable(HelloWorld helloworld.cpp)

target_link_libraries(HelloWorld PRIVATE 
    $<TARGET_NAME_IF_EXISTS:SDL2::SDL2main>
    $<IF:$<TARGET_EXISTS:SDL2::SDL2>,SDL2::SDL2,SDL2::SDL2-static> 
    $<IF:$<TARGET_EXISTS:SDL2_ttf::SDL2_ttf>,SDL2_ttf::SDL2_ttf,SDL2_ttf::SDL2_ttf-static>
    imgui::imgui
)