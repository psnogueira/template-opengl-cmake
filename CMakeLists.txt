# # # # # # # # # # # # # # # # #
#   Projeto base para OpenGL    #
#   com CMake                   #
# # # # # # # # # # # # # # # # #
#                               #
#       Autor: psnogueira       #
#       Data: 2025-07-17        #
#       Licença: MIT            #
#                               #
#                        v1.0.1 #
# # # # # # # # # # # # # # # # #

cmake_minimum_required(VERSION 3.16)

set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")     # Esse comando é para o Visual Studio, se você estiver usando outro compilador, remova essa linha.
set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Release>:Release>") # Esse comando é para o Visual Studio, se você estiver usando outro compilador, remova essa linha.

project(MeuProjeto VERSION 1.0.1 LANGUAGES C CXX)

# Habilita testes para o projeto.
include(CTest)
enable_testing()

add_executable("${CMAKE_PROJECT_NAME}")

set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
set(GLFW_INSTALL OFF CACHE BOOL "" FORCE)
add_subdirectory(include/glfw-3.4)		# Abre a janela.
add_subdirectory(include/glad)			# Carrega as funcoes OpenGL.

# Define MY_SOURCES como uma lista de todos os arquivos fonte do meu projeto
file(GLOB_RECURSE MY_SOURCES CONFIGURE_DEPENDS "${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp")

set_property(TARGET "${CMAKE_PROJECT_NAME}" PROPERTY CXX_STANDARD 17)

target_sources("${CMAKE_PROJECT_NAME}" PRIVATE ${MY_SOURCES} )

if(MSVC) # Se você estiver usando o Visual Studio.
	target_compile_definitions("${CMAKE_PROJECT_NAME}" PUBLIC _CRT_SECURE_NO_WARNINGS)
	
	set_property(TARGET "${CMAKE_PROJECT_NAME}" PROPERTY MSVC_RUNTIME_LIBRARY "MultiThreadedDebug<$<CONFIG:Debug>:Debug>")
	set_property(TARGET "${CMAKE_PROJECT_NAME}" PROPERTY MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Release>:Release>")
endif()

# Se você tiver um diretório com arquivos para incluir (ex: particle.h), adicione-o aqui.
target_include_directories("${CMAKE_PROJECT_NAME}" PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/include/")

target_link_libraries("${CMAKE_PROJECT_NAME}" PRIVATE 
	glfw 
	glad
)