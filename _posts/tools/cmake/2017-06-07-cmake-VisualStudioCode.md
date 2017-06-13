---
layout: page
title: Visual Studio Code cmake
description: "Instructions on how to use cmake on windows visual studio code."
category: 工具
tags: [cmake, VisualStudioCode]
---

#CMakelists.txt
```
cmake_minimum_required(VERSION 3.7)

project(ATSUnitTest CXX)

INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR}) 
INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR}\\..\\..\\gmock\\include)
INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR}\\..\\..\\winInterface)
INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR}\\..\\..\\..\\ATS2PA\\src)

LINK_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR}\\..\\..\\gmock)

#MFC
add_definitions(-D_AFXDLL)
#1 为静态链接，2为动态链接
set(CMAKE_MFC_FLAG 2)
# force Unicode over Multi-byte
#if(COMPILER_MSVC)
add_definitions(-DUNICODE -D_UNICODE)
set(CMAKE_C_FLAGS_DEBUG "${CMAKE_C_FLAGS_DEBUG} /W3 /MTd")
set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} /MT")
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} /MTd")
#endif()

set(LIBNAME "gmock.lib")
set(ATS_SRC_DIR "../../../ATS2PA/src/")

add_definitions(-DCOMPILE_UNIT_TESTS)

add_executable(ATSUnitTest ../../main.cpp
    taskunittest.cpp
    ${ATS_SRC_DIR}/ats/ats.cpp
    ${ATS_SRC_DIR}/ats/task.cpp
    ${ATS_SRC_DIR}/ats/atspackage.cc
    ${ATS_SRC_DIR}/utils/crc.cc
    ${ATS_SRC_DIR}/utils/timer.cpp)

target_link_libraries(ATSUnitTest debug gmock.lib)

```

#Run command
```
mkdir build
cd build
cmake ..
cd ..
cmake --build build --target ALL_BUILD
```