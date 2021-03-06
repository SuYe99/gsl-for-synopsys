cmake_minimum_required(VERSION 3.8 FATAL_ERROR)
include(gsl)

set(project_name "multilarge_nlinear_test")
project("${project_name}")
set(project_version "1.0")

set(CMAKE_INSTALL_PREFIX ${CNNSDK_INSTALL_DIR})
find_package(ev_gsl_includes 1.0 REQUIRED)
find_package(gsl_test 1.0 REQUIRED)
find_package(ieee-utils 1.0 REQUIRED)
find_package(err 1.0 REQUIRED)
find_package(evthreads 1.0 REQUIRED)
find_package(multilarge_nlinear 1.0 REQUIRED)

set(GSL_SRC_FILES ../test.c)
add_executable(${project_name} ${GSL_SRC_FILES})

target_link_libraries(${project_name} ev_gsl_includes::ev_gsl_includes)
target_link_libraries(${project_name} gsl_test::gsl_test)
target_link_libraries(${project_name} ieee-utils::ieee-utils)
target_link_libraries(${project_name} err::err)
target_link_libraries(${project_name} evthreads::evthreads)
target_link_libraries(${project_name} multilarge_nlinear::multilarge_nlinear)

target_include_directories(${project_name}
    PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
)

install(CODE "message(\"Nothing to do\")")
