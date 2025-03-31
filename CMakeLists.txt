cmake_minimum_required(VERSION 3.10)
project(ChessEngine C)

set(CMAKE_C_STANDARD 11)

#Enable Optimizations for release mode
set(CMAKE_C_FLAGS_RELEASE "-Ofast")

#add executable
add_executable(chess_engine src/bbc.c)

#set compiler based flags based on the build type(Release or debug)

target_compile_options(chess_engine PRIVATE
 $<$<CONFIG:Release>:-Ofast>
 $<$<CONFIG:Debug>:-g -O0>
)

#Windows specific settingd (for MINGW)
if(MINGW)
set(CMAKE_C_FLAGS_RELEASE "-Ofast")
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

endif()
