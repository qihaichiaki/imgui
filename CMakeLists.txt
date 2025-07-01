project(imgui)

file(GLOB SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp")

# 添加此宏方便imgui做静态库链接到动态库后, 也能将接口暴露出去给其他客户端使用
if(MSVC)
    add_definitions(
        "-DIMGUI_API=__declspec(dllexport)"
    )
endif()

add_library(${PROJECT_NAME} STATIC
    ${SOURCES}
)

target_include_directories(${PROJECT_NAME} PUBLIC
    "${CMAKE_CURRENT_SOURCE_DIR}"
)
