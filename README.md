#Отчет по лабораторной работе номер 4


##ФАЙЛ .travis.yml

language: cpp
script:
- cd formatter_lib
- cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
- cmake --build _build
- cd ..
- cd formatter_ex_lib
- cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
- cmake --build _build
- cd ..
- cd hello_world_application
- cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
- cmake --build _build
- cd ..
- cd solver_lib
- cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
- cmake --build _build
- cd ..
- cd solver_application
- cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
- cmake --build _build
addons:
  apt:
    sources:
      - george-edison55-precise-backports
    packages:
      - cmake
      - cmake-data
      - mingw-w64
      
##Статус сборки travis
[![Build Status](https://travis-ci.com/Nikita0042/lab04.svg?branch=master)](https://travis-ci.com/Nikita0042/lab04)
      
##Файл .appveyor.yml

image: Visual Studio 2015

init:
    - git config --global core.autocrlf input

clone_folder: c:\projects\my-prj 
shallow_clone: true     

matrix:
    fast_finish: false     

platform:
    - x64
    - x86

configuration:
    - Release

environment:
    matrix:
        - TOOLCHAIN: msvc14

build_script:
    - cd ./formatter_lib
    - cmake -H. -B_build
    - cmake --build _build

    - cd ../formatter_ex_lib
    - cmake -H. -B_build
    - cmake --build _build

    - cd ../solver_lib
    - cmake -H. -B_build
    - cmake --build _build

    - cd ../solver_application
    - cmake -H. -B_build
    - cmake --build _build

    - cd ../hello_world_application
    - cmake -H. -B_build
    - cmake --build _build

##Статус сборки Appveyor
[![Build status](https://ci.appveyor.com/api/projects/status/0krxmv9rf002k4gs?svg=true)](https://ci.appveyor.com/project/Nikita0042/lab04)
