# Отчет по лабораторной работе номер 4


## Файл .travis.yml
	
	language: cpp
	script:
	- cd formatter_lib # Переходим в папку форматтер либ 
	- cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install # Задаем 	папку сборки _build и переменную
	- cmake --build _build # Делает сборку
	- cd ..
	- cd formatter_ex_lib # Переходим в папку форматтер екс либ
	- cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install # Задаем 	папку сборки _build и переменную
	- cmake --build _build # Делает сборку
	- cd ..
	- cd hello_world_application # Переходим в папку хеллоу ворлд 	апликэйшн
	- cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install # Задаем 	папку сборки _build и переменную
	- cmake --build _build # Делает сборку
	- cd ..
	- cd solver_lib # Переходим в папку солвер либ
	- cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install # Задаем 	папку сборки _build и переменную
	- cmake --build _build # Делает сборку
	- cd ..
	- cd solver_application # Переходим в папку солвер апликэйшн
	- cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install # Задаем 	папку сборки _build и переменную
	- cmake --build _build # Делает сборку
	matrix:
	  include:
	    - os: linux # Операционная система линукс
	      addons:
	        apt:
	          sources: # Подгружаем пакеты в трэвис
	            - sourceline: 'ppa:ubuntu-toolchain-r/test'
	          packages:
	            - clang-8 # Добавление пакета
	      env:
	        - MATRIX_EVAL="CC=clang-8 CXX=clang++-8"
	    - os: linux # Операционная система линукс
	      addons:
	        apt:
	          sources: # Подгружаем пакеты в трэвис
	            - sourceline: 'ppa:ubuntu-toolchain-r/test'
	          packages:
	            - g++-9 # Добавление пакета
	      env:
	        - MATRIX_EVAL="CC=gcc-9 CXX=g++-9" # Указываем версии компиляторов

before_install:
  - eval "${MATRIX_EVAL}" # compiler: clang было в избытке - его эффекты были отменены уловкой eval "${MATRIX_EVAL}"
	      
## Статус сборки travis

[![Build Status](https://travis-ci.com/Nikita0042/lab04.svg?branch=master)](https://travis-ci.com/Nikita0042/lab04)
      
## Файл .appveyor.yml

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
	
## Статус сборки Appveyor

[![Build status](https://ci.appveyor.com/api/projects/status/0krxmv9rf002k4gs?svg=true)](https://ci.appveyor.com/project/Nikita0042/lab04)
