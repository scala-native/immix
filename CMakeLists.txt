cmake_minimum_required(VERSION 3.4.3)
project(immix C)

# Colors when compiling with clang
set(CMAKE_CXX_FLAGS "-fdiagnostics-color=always")
set(CMAKE_C_FLAGS "-fdiagnostics-color=always")

# LLVM
# find_package(LLVM REQUIRED)
# # HACK: I'm using all. I need to ask on the mailing list how to fix this.
# llvm_map_components_to_libnames(LLVM_LIBS AllTargetsAsmPrinters 
#     AllTargetsAsmParsers Core Support ORCJIT MCJIT ExecutionEngine
#     ASMPrinter CodeGen AllTargetsDescs AllTargetsInfos TransformUtils Object
#     NVPTXCodeGen ipo Passes Analysis
#     nativecodegen MC)
# 
# # FLEX AND BISON
# find_package(BISON)
# find_package(FLEX)
# bison_target(Parser src/parser.yy ${CMAKE_SOURCE_DIR}/src/parser.generated.cpp COMPILE_FLAGS -v)
# flex_target(Lexer src/lexer.l  ${CMAKE_SOURCE_DIR}/src/lexer.generated.cpp)
# add_flex_bison_dependency(Lexer Parser)


# INCLUDES AND SOURCES
#include_directories(include ${LLVM_INCLUDE_DIRS})

add_library(immix
    SHARED 
complex.c
dirent.c
dyndispatch.c
eh.cpp
fcntl.c
grp.c
limits.c
optional
perfecthashmap.h
platform.c
posix
posix.c
pwd.c
README.md
stat.c
statvfs.c
tags
time.c
time.cpp
types.h
unistd.c
unwind.c
utime.c
wrap.c
# none
# gc/none/gc.c
# boehm
# gc/boehm/gc.c
# immix
gc/immix/Allocator.c
gc/immix/Allocator.h
gc/immix/Block.c
gc/immix/Block.h
gc/immix/Constants.h
gc/immix/datastructures
gc/immix/GCTypes.h
gc/immix/headers
gc/immix/Heap.c
gc/immix/Heap.h
gc/immix/ImmixGC.c
gc/immix/LargeAllocator.c
gc/immix/LargeAllocator.h
gc/immix/Line.h
gc/immix/Log.h
gc/immix/Marker.c
gc/immix/Marker.h
gc/immix/Memory.h
gc/immix/Object.c
gc/immix/Object.h
gc/immix/StackoverflowHandler.c
gc/immix/StackoverflowHandler.h
gc/immix/StackTrace.h
gc/immix/State.c
gc/immix/State.h
gc/immix/utils)
set_target_properties(immix PROPERTIES C_STANDARD 99)

# add_executable(sxhc
#     src/main.cpp
#     src/RuntimeDebugBuilder.cpp
#     src/stgir.cpp
#     ${BISON_Parser_OUTPUTS}
#     ${FLEX_Lexer_OUTPUTS}
#     )
# 
# target_link_libraries(sxhc ${LLVM_LIBS}  -lstdc++ stgruntime)
# set_target_properties(sxhc PROPERTIES CXX_STANDARD 14)
# 
# # CLANG FORMAT
# file(GLOB_RECURSE ALL_SOURCE_FILES *.cpp *.h)
# 
# find_program(CLANG_FORMAT clang-format)
# add_custom_target(
#         format
#         COMMAND ${CLANG_FORMAT}
#         -style=LLVM
#         -i
#         ${ALL_SOURCE_FILES}
# )
# 
# # libstg
# add_library(stgruntime
#     SHARED lib/libstg.c)
# set_target_properties(stgruntime PROPERTIES C_STANDARD 99)
# 
# 
# 
# #sxhcpasses, so they can be loaded into opt
# add_library(sxhcpasses SHARED lib/optimizer.cpp)
# target_link_libraries(sxhcpasses ${LLVM_LIBS} -lstdc++)
# set_target_properties(sxhcpasses PROPERTIES CXX_STANDARD 14)
# 
# # DOXYGEN
# # first we can indicate the documentation build as an option and set it to ON by default
# option(BUILD_DOC "Build documentation" OFF)
# 
# # check if Doxygen is installed
# find_package(Doxygen)
# if (DOXYGEN_FOUND)
#     # set input and output files
#     set(DOXYGEN_IN ${CMAKE_CURRENT_SOURCE_DIR}/docs/Doxyfile.in)
#     set(DOXYGEN_OUT ${CMAKE_CURRENT_BINARY_DIR}/Doxyfile)
# 
#     # request to configure the file
#     configure_file(${DOXYGEN_IN} ${DOXYGEN_OUT} @ONLY)
#     message("Doxygen build started")
# 
#     # note the option ALL which allows to build the docs together with the application
#     add_custom_target(doc
#         COMMAND ${DOXYGEN_EXECUTABLE} ${DOXYGEN_OUT}
#         WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
#         COMMENT "Generating API documentation with Doxygen"
#         VERBATIM )
# else (DOXYGEN_FOUND)
#   message("Doxygen need to be installed to generate the doxygen documentation")
# endif (DOXYGEN_FOUND)
# 
# # add stgruntime to sxhc so the JIT has access to all functions from stgruntime.
# target_link_libraries(sxhc stgruntime)
