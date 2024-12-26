cmake_minimum_required(VERSION 3.22)

#-------------------------------------------------------------------------------
#   project setup
#-------------------------------------------------------------------------------

set(target_name int_sin)

project(${target_name} Fortran C)

#-------------------------------------------------------------------------------
#   target setup
#-------------------------------------------------------------------------------

add_library(${target_name})

target_sources(${target_name}
    PRIVATE
        src/int_sin.f90
)

#-------------------------------------------------------------------------------
#   target setup
#-------------------------------------------------------------------------------

add_executable(${target_name}_f)

target_sources(${target_name}_f
    PRIVATE
        src/test_int_sin.f90
)

target_link_libraries(${target_name}_f
    PRIVATE
        ${target_name}
)

#-------------------------------------------------------------------------------
#   target setup
#-------------------------------------------------------------------------------

add_executable(${target_name}_c)

target_sources(${target_name}_c
    PRIVATE
        src/test_int_sin.c
)

target_link_libraries(${target_name}_c
    PRIVATE
        ${target_name}
)
