cmake_minimum_required(VERSION 3.9)

project("spine-c" LANGUAGES CXX C)

file(GLOB SPINE_INCLUDES "spine-c/include/**/*.h")
file(GLOB SPINE_SOURCES "spine-c/src/**/*.c" "spine-c/src/**/*.cpp")

add_library(spine-c STATIC ${SPINE_SOURCES} ${SPINE_INCLUDES})

if(MSVC)

else()
    target_compile_options(spine-c PRIVATE "-fPIC")
endif()

target_include_directories(spine-c PUBLIC spine-c)
install(TARGETS spine-c DESTINATION dist/lib)
install(FILES ${INCLUDES} DESTINATION dist/include)
