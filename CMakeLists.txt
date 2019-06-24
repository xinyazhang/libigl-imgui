cmake_minimum_required(VERSION 3.1)

# Note: this project is supposed to create a static library, i.e. a collection of .o/.obj files
#       we delegated external dependencies to the project that uses this library.
#       User of this library is supposed to 
#       1. Find the include dir of glad, and link to it:w
#       2. Find the include dir of glfw, and link to it:w

add_library(imgui STATIC
		../imgui/imgui.cpp
		../imgui/imgui.h
		../imgui/imgui_demo.cpp
		../imgui/imgui_draw.cpp
		../imgui/imgui_internal.h
		../imgui/imgui_widgets.cpp
		../imgui/imstb_rectpack.h
		../imgui/imstb_textedit.h
		../imgui/imstb_truetype.h
		../imgui/examples/imgui_impl_opengl3.cpp
		../imgui/examples/imgui_impl_opengl3.h
		imgui_impl_glfw.cpp
		imgui_impl_glfw.h
)

target_include_directories(imgui PRIVATE ../imgui)
target_include_directories(imgui PUBLIC . .. ../imgui/examples)
target_compile_definitions(imgui PUBLIC -DIMGUI_IMPL_OPENGL_LOADER_GLAD)

# target_link_libraries(imgui PRIVATE glad glfw)
