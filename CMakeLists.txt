cmake_minimum_required(VERSION 2.8)

project(ITTI)

set(ITTICFiles
    ${CMAKE_CURRENT_SOURCE_DIR}/ittiFiles/inc/backtrace.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ittiFiles/inc/bstrlib.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ittiFiles/inc/intertask_interface.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ittiFiles/inc/intertask_interface_dump.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ittiFiles/inc/memory_pools.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ittiFiles/inc/signals.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ittiFiles/inc/timer.c
    ${CMAKE_CURRENT_SOURCE_DIR}/ittiFiles/inc/dynamic_memory_check.c
)

add_library(ITTI ${ITTICFiles})
set(ITTI_LIB ${ITTI})
set(LFDS ${CMAKE_CURRENT_SOURCE_DIR}/ittiFiles/lib/liblfds611.a)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/ittiFiles/inc)
add_executable(ITTIDEMO
    ${CMAKE_CURRENT_SOURCE_DIR}/main.c
    ${ITTICFiles}
)
target_link_libraries(ITTIDEMO
    ${LFDS}
    pthread rt
)

