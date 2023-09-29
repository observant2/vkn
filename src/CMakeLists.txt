
# Add source to this project's executable.
add_executable(vulkan_guide
    main.cpp
    vk_engine.cpp
    vk_engine.h
    vk_types.h
    vk_initializers.cpp
    vk_initializers.h)


find_package(SDL2 CONFIG REQUIRED)
find_package(fmt CONFIG REQUIRED)
find_package(Vulkan REQUIRED)
find_package(vk-bootstrap CONFIG REQUIRED)

set_property(TARGET vulkan_guide PROPERTY VS_DEBUGGER_WORKING_DIRECTORY "$<TARGET_FILE_DIR:vulkan_guide>")

target_include_directories(vulkan_guide PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}")
target_link_libraries(vulkan_guide PRIVATE vma glm tinyobjloader imgui stb_image)

target_link_libraries(vulkan_guide PRIVATE SDL2::SDL2 Vulkan::Vulkan vk-bootstrap::vk-bootstrap)
target_link_libraries(vulkan_guide PRIVATE fmt::fmt)

add_dependencies(vulkan_guide Shaders)
