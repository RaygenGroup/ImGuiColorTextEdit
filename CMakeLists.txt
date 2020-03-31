project (ImGuiColorTextEdit)

set(SOURCE_FILES
	TextEditor.cpp

)
set(HEADER_FILES
	TextEditor.h
)

add_library(ImGuiColorTextEdit ${SOURCE_FILES} ${HEADER_FILES})

target_include_directories(ImGuiColorTextEdit PRIVATE ${DEPENDENCIES_DIRECTORY}/imgui)
target_include_directories(ImGuiColorTextEdit PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})


target_link_libraries(ImGuiColorTextEdit
	ImGui
)


if(MSVC)
	target_compile_options(ImGui PRIVATE "/MP")
endif()

# enforce cpp20
set_property(TARGET ImGuiColorTextEdit PROPERTY CXX_STANDARD 20)
set_property(TARGET ImGuiColorTextEdit PROPERTY CXX_STANDARD_REQUIRED ON)

source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR} PREFIX ${PROJECT_NAME} FILES ${HEADER_FILES} ${SOURCE_FILES})
