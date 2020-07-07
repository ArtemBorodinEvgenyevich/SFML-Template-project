# SFML Template Project

## Description: 
A project to be used as a template for c++ SFML application development.

Includes precompiled SMFL 2.5.1 libs and headers for **Linux(x64)** and **Windows(x64|x86)**.
It is highly recommended to compile SFML from source to avoid platform dependent issues.

If you want to use SFML compiled from source, simply put the compiled one in ``vendor/[PLATFORM]-SFML-2.1.1-[EXTENSION]``
similarly to existing dirs.

## Requirements:

### Build system
* CMake - version minimum 3.13
* GNU Make - version 4.2.1

### Compilers:
#### Linux
* GCC - version 8.3.0 
#### Windows
* MinGW: (Supported both **w32** and **w64**)
    * mingw-w32
    * mingw-w64 

### Additional dependencies:
In case you would like to compile SFML from source, you should have installed libraries it relies on:
* [OpenAL-Soft](https://github.com/kcat/openal-soft)
* [stb_image.h](https://github.com/nothings/stb#stb)     
* [freetype](https://www.freetype.org/download.html)
* [libvorbis](https://github.com/gypified/libvorbis)
* [libflac](https://github.com/xiph/flac)
