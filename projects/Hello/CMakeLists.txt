cmake_minimum_required(VERSION 3.7.2)

project(Hello C) # create a new C project called 'init' 


add_executable(Hello src/main.c) # add files to our project. Paths are relative to this file.

target_link_libraries(Hello sel4muslcsys  muslc) # we need to link against the standard C lib for printf


# Set this image as the rootserver
DeclareRootserver(Hello)

