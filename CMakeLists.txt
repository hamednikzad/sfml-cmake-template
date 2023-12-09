message(Version: ${CMAKE_VERSION})
cmake_minimum_required(VERSION 3.26)
project(sfml-cmake-template LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)

set(SFML_PATH C:/OpenGl/Engines/SFML-2.6.1)

include_directories(${SFML_PATH}/include)

add_executable(${PROJECT_NAME} src/main.cpp)

file(GLOB LIB_SRC ${SFML_PATH}/lib/*.a)
#message(LIBFILE=${LIB_SRC})
target_link_libraries(${PROJECT_NAME} ${LIB_SRC})

file(GLOB DLL_SRC ${SFML_PATH}/bin/*.dll)
foreach (dllFile ${DLL_SRC})
    configure_file(${dllFile} ${CMAKE_CURRENT_BINARY_DIR} COPYONLY)
endforeach()


