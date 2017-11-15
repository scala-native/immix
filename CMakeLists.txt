cmake_minimum_required(VERSION 3.6)
PROJECT(Immix)


set(CMAKE_CXX_STANDARD 11)

add_library(Immix src/
        src/datastructures/Bitmap.c
        src/datastructures/Bitmap.h
        src/datastructures/BlockList.c
        src/datastructures/BlockList.h
        src/datastructures/Stack.c
        src/datastructures/Stack.h
        src/headers/BlockHeader.h
        src/headers/LineHeader.h
        src/headers/ObjectHeader.h
        src/utils/MathUtils.h
        src/Allocator.c
        src/Allocator.h
        src/Block.c
        src/Block.h
        src/Constants.h
        src/GCTypes.h
        src/Heap.c
        src/Heap.h
        src/ImmixGC.c
        src/LargeAllocator.c
        src/LargeAllocator.h
        src/Line.h
        src/Log.h
        src/Marker.c
        src/Marker.h
        src/Memory.h
        src/Object.c
        src/Object.h
        src/StackoverflowHandler.c
        src/StackoverflowHandler.h
        src/StackTrace.h
        src/State.c
        src/State.h)

set_target_properties(Immix PROPERTIES LINKER_LANGUAGE C)
set_target_properties(Immix PROPERTIES ARCHIVE_OUTPUT_DIRECTORY build)


