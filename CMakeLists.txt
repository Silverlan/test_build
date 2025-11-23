cmake_minimum_required(VERSION 3.3)

message(STATUS "CMake version: ${CMAKE_VERSION}")
set(CMAKE_EXPERIMENTAL_CXX_IMPORT_STD "d0edc3af-4c50-42ea-a356-e2862fe7a444")
set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_MODULE_STD 1)

get_filename_component(_cxx_name "${CMAKE_CXX_COMPILER}" NAME)
string(TOLOWER "${_cxx_name}" _cxx_name_lower)
if (_cxx_name_lower MATCHES "clang")
    # Required for "import std" when using clang compiler
    add_compile_options(-stdlib=libstdc++)
    add_link_options(-stdlib=libstdc++)
endif()

add_subdirectory(luabind)
