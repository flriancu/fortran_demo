cmake_minimum_required(VERSION 3.22)

#-------------------------------------------------------------------------------
#   project setup
#-------------------------------------------------------------------------------

set(target_name fortran_test)

project(${target_name} Fortran C CXX)

add_executable(${target_name})

target_sources(${target_name}
    PRIVATE
        src/int_sin.f90
)
