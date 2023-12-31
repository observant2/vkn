find_package(Vulkan REQUIRED)

add_library(glm INTERFACE)
add_library(vma INTERFACE)

add_library(stb_image INTERFACE)

add_library(tinyobjloader STATIC)

#both vma and glm and header only libs so we only need the include path
target_include_directories(vma INTERFACE vma)
target_include_directories(glm INTERFACE glm)

target_sources(tinyobjloader PRIVATE 
    tinyobjloader/tiny_obj_loader.h
    tinyobjloader/tiny_obj_loader.cc
    )

target_include_directories(tinyobjloader PUBLIC tinyobjloader)


find_package(sdl2 CONFIG REQUIRED)

add_library(imgui STATIC)

target_include_directories(imgui PUBLIC imgui)

target_sources(imgui PRIVATE 
    imgui/imgui.h
    imgui/imgui.cpp

    imgui/imgui_demo.cpp
    imgui/imgui_draw.cpp
    imgui/imgui_widgets.cpp

    imgui/imgui_impl_vulkan.cpp
    imgui/imgui_impl_sdl.cpp
    )

target_link_libraries(imgui PUBLIC Vulkan::Vulkan)

target_link_libraries(imgui PUBLIC SDL2::SDL2)

target_include_directories(stb_image INTERFACE stb_image)
