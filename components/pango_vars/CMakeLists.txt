get_filename_component(COMPONENT ${CMAKE_CURRENT_LIST_DIR} NAME)

target_sources( ${COMPONENT}
PRIVATE
    ${CMAKE_CURRENT_LIST_DIR}/src/vars.cpp
)

target_include_directories(${COMPONENT} PUBLIC "${CMAKE_CURRENT_LIST_DIR}/include")
target_link_libraries(${COMPONENT} PUBLIC pango_core)


find_package(Catch2 2 QUIET)
if(Catch2_FOUND)
    add_executable(test_vars ${CMAKE_CURRENT_LIST_DIR}/tests/test_all.cpp)
    target_link_libraries(test_vars PRIVATE Catch2::Catch2 ${COMPONENT})
endif()
