cmake_minimum_required(VERSION 3.13)
project(SFML-Template-project)

set(CMAKE_CXX_STANDARD 14)

# Uncomment to make a 'Make' verbose
#set(CMAKE_VERBOSE_MAKEFILE ON)

# Setup for UNIX-like system
if (UNIX)
    message("--|| Using Unix-like OS ||--")

    # Set 3rd party libraries paths
    set(SFML_INCLUDE_DIR "${CMAKE_CURRENT_LIST_DIR}/vendor/UNIX-SFML-2.5.1/include")
    set(SFML_LIBRARY_DIR "${CMAKE_CURRENT_LIST_DIR}/vendor/UNIX-SFML-2.5.1/lib")
    set(SFML_DIR "${CMAKE_CURRENT_LIST_DIR}/vendor/UNIX-SFML-2.5.1/lib/cmake/SFML")

    # Link all *.so files
    link_directories(SFML_LIBRARY_DIR)

# Setup for Windows system
elseif(WIN32)
    message("--|| Using Windows OS ||--")

    # Set 3rd party libraries paths
    if(MINGW AND NOT CMAKE_CL_64)
        message(--|| Using MinGW x86 ||--)

        set(SFML_DIR "${CMAKE_CURRENT_LIST_DIR}/vendor/WIN-SFML-2.5.1-x86/lib/cmake/SFML")
        set(SFML_BINARY_DIR "${CMAKE_CURRENT_LIST_DIR}/vendor/WIN-SFML-2.5.1-x86/bin")
        set(SFML_INCLUDE_DIR "${CMAKE_CURRENT_LIST_DIR}/vendor/WIN-SFML-2.5.1-x86/include")
        set(SFML_LIBRARY_DIR "${CMAKE_CURRENT_LIST_DIR}/vendor/WIN-SFML-2.5.1-x86/lib")

    elseif(MINGW AND CMAKE_CL_64)
        message(--|| Using MinGW x64 ||--)

        set(SFML_DIR "${CMAKE_CURRENT_LIST_DIR}/vendor/WIN-SFML-2.5.1/lib/cmake/SFML")
        set(SFML_BINARY_DIR "${CMAKE_CURRENT_LIST_DIR}/vendor/WIN-SFML-2.5.1/bin")
        set(SFML_INCLUDE_DIR "${CMAKE_CURRENT_LIST_DIR}/vendor/WIN-SFML-2.5.1/include")
        set(SFML_LIBRARY_DIR "${CMAKE_CURRENT_LIST_DIR}/vendor/WIN-SFML-2.5.1/lib")

    endif()

    # Copy all *.dll files to compiled project binaries
    file(GLOB SFML_DLLS "${SFML_BINARY_DIR}/*.dll")
    file(COPY ${SFML_DLLS} DESTINATION ${CMAKE_CURRENT_BINARY_DIR})

    # GARBAGE -> Remove
    #link_directories(SFML_BINARY_DIR SFML_LIBRARY_DIR)

endif()

include_directories(SFML_INCLUDE_DIR)
find_package(SFML 2.5.1 COMPONENTS system window graphics network audio)

if(SFML_FOUND)
    message(STATUS "SFML_INCLUDE_DIR: ${SFML_INCLUDE_DIR}")
    message(STATUS "SFML_LIBRARIES: ${SFML_LIBRARIES}")
    message(STATUS "SFML_VERSION: ${SFML_VERSION}")
endif()

add_executable(SFML-Template-project main.cpp)
target_link_libraries (SFML-Template-project sfml-graphics sfml-window sfml-system)
