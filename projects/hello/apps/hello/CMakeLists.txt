cmake_minimum_required(VERSION 3.7.2)

project(Hello C) # create a new C project called 'init' 

find_package(musllibc REQUIRED)
find_package(util_libs REQUIRED)
find_package(seL4_libs REQUIRED)
#find_package(sel4_projects_libs REQUIRED)
musllibc_setup_build_environment_with_sel4runtime()
sel4_import_libsel4()
util_libs_import_libraries()
sel4_libs_import_libraries()

add_executable(Hello src/main.c) # add files to our project. Paths are relative to this file.

target_link_libraries(Hello PUBLIC muslc sel4runtime sel4muslcsys)

# Set this image as the rootserver
include(rootserver)
DeclareRootserver(Hello)