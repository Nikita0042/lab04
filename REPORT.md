

# Part1 - File formatter_lib/CMakeLists.txt:

	cmake_minimum_required(VERSION 3.4)
	set(CMAKE_CXX_STANDARD 11)
	set(CMAKE_CXX_STANDARD_REQUIRED ON)
	project(formatter)
	add_library(formatter STATIC formatter.h formatter.cpp)

# Part1 - Terminal:
######	nikita@nikita-VirtualBox:~$ cd Nikita0042
######	nikita@nikita-VirtualBox:~/Nikita0042$ cd workspace
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace$ cd scripts
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/scripts$ ls
	activate  exports
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/scripts$ source exports
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/scripts$ source activate
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/scripts$ cd ..

######	nikita@nikita-VirtualBox:~/Nikita0042/workspace$ cd projects

######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects$ mkdir lab03
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects$ cd ..

######	nikita@nikita-VirtualBox:~/Nikita0042/workspace$ git clone https://github.com/tp-labs/lab03 projects/lab03
	Клонирование в «projects/lab03»…
	remote: Enumerating objects: 3, done.
	remote: Counting objects: 100% (3/3), done.
	remote: Compressing objects: 100% (3/3), done.
	remote: Total 91 (delta 0), reused 0 (delta 0), pack-reused 88
	Распаковка объектов: 100% (91/91), 1.03 MiB | 548.00 KiB/s, готово.

######	nikita@nikita-VirtualBox:~/Nikita0042/workspace$ cd projects
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects$ cd lab03
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03$ ls
	CMakeLists.txt    hello_world_application  README.md
	formatter_ex_lib  LICENSE                  solver_application
	formatter_lib     preview.png              solver_lib

######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03$ cd formatter_lib

######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/formatter_lib$ nano CMakeLists.txt
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/formatter_lib$ ls
	CMakeLists.txt  formatter.cpp  formatter.h

######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/formatter_lib$ sudo snap install cmake
	[sudo] пароль для nikita: 
	ошибка: This revision of snap "cmake" was published using classic
              confinement and thus may perform arbitrary system changes
              outside of the security sandbox that snaps are usually confined
              to, which may put your system at risk.

              If you understand and want to proceed repeat the command
              including --classic.
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/formatter_lib$ sudo snap install cmake --classic
	cmake 3.20.1 от Crascit✓ установлен

######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/formatter_lib$ sudo apt install g++

######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/formatter_lib$ sudo install make

######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/formatter_lib$ cmake -H. -B_build
	-- The C compiler identification is GNU 9.3.0
	-- The CXX compiler identification is GNU 9.3.0
	-- Detecting C compiler ABI info
	-- Detecting C compiler ABI info - done
	-- Check for working C compiler: /usr/bin/cc - skipped
	-- Detecting C compile features
	-- Detecting C compile features - done
	-- Detecting CXX compiler ABI info
	-- Detecting CXX compiler ABI info - done
	-- Check for working CXX compiler: /usr/bin/c++ - skipped
	-- Detecting CXX compile features
	-- Detecting CXX compile features - done
	-- Configuring done
	-- Generating done
	-- Build files have been written to: /home/nikita/Nikita0042/workspace/projects/lab03/formatter_lib/_build

######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/formatter_lib$ cmake --build _build
	[ 50%] Building CXX object CMakeFiles/formatter.dir/formatter.cpp.o
	[100%] Linking CXX static library libformatter.a
	[100%] Built target formatter

######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/formatter_lib$ ls
	_build   CMakeCache.txt  cmake_install.cmake  formatter.cpp  Makefile
	_build2  CMakeFiles      CMakeLists.txt       formatter.h
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/formatter_lib$ cd _build
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/formatter_lib/_build$ ls
	CMakeCache.txt  CMakeFiles  cmake_install.cmake  libformatter.a  Makefile


# Part2 - File formatter_ex_lib/CMakeLists.txt:

	cmake_minimum_required(VERSION 3.4)
	set(CMAKE_CXX_STANDARD 11)
	set(CMAKE_CXX_STANDARD_REQUIRED ON)
	project(formatter_ex)
	include_directories(../formatter_lib)
	add_subdirectory(../formatter_lib ~/Nikita0042/workspace/projects/lab03/formatter_lib/_build)
	add_library(formatter_ex STATIC formatter_ex.h formatter_ex.cpp)
	target_link_libraries(formatter_ex formatter)

# Part2 - Terminal:

######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/formatter_ex_lib$ nano CMakeLists.txt
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/formatter_ex_lib$ cmake -H. -B_build
	-- Configuring done
	-- Generating done
	-- Build files have been written to: /home/nikita/Nikita0042/workspace/projects/lab03/formatter_ex_lib/_build
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/formatter_ex_lib$ cmake --build _build
	Consolidate compiler generated dependencies of target formatter
	[ 25%] Building CXX object _build/CMakeFiles/formatter.dir/formatter.cpp.o
	[ 50%] Linking CXX static library libformatter.a
	[ 50%] Built target formatter
	[ 75%] Building CXX object CMakeFiles/formatter_ex.dir/formatter_ex.cpp.o
	[100%] Linking CXX static library libformatter_ex.a
	[100%] Built target formatter_ex
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/formatter_ex_lib$ 


# Part3 - File hello_world_application/CMakeLists.txt:

	cmake_minimum_required(VERSION 3.4)
	project(hello_world)
	include_directories(../formatter_ex_lib)
	add_subdirectory(../formatter_ex_lib ~/Nikita0042/workspace/projects/lab03/formatter_ex_lib/_build)
	add_executable(hello_world hello_world.cpp)
	target_link_libraries(hello_world formatter_ex)

# Part3 - File solver_lib/CMakeLists.txt:

	cmake_minimum_required(VERSION 3.4)
	project(solver_lib)
	add_library(solver_lib STATIC solver.h solver.cpp)

# Part3 - File solver_application/CMakeLists.txt:

	cmake_minimum_required(VERSION 3.4)
	project(solver)
	include_directories(../formatter_ex_lib)
	add_subdirectory(../formatter_ex_lib ~/Nikita0042/workspace/projects/lab03/formatter_ex_lib/_build)
	include_directories(../solver_lib)
	add_subdirectory(../solver_lib ~/Nikita0042/workspace/projects/lab03/solver_lib/_build)
	add_executable(solver equation.cpp)
	target_link_libraries(solver formatter_ex)
	target_link_libraries(solver solver_lib)


# Part3 - Terminal:

######	nikita@nikita-VirtualBox:~$ cd Nikita0042
######	nikita@nikita-VirtualBox:~/Nikita0042$ cd workspace
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace$ cd projects
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects$ cd lab03
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03$ ls
	_build          formatter_ex_lib         preview.png  solver_application
	CMakeCache.txt  formatter_lib            README.md    solver_lib
	CMakeFiles      hello_world_application  report.html
	CMakeLists.txt  LICENSE                  report.txt
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03$ cd hello_world_application
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/hello_world_application$ nano CMakeLists.txt
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/hello_world_application$ cmake -H. -B_build
	-- Configuring done
	-- Generating done
	-- Build files have been written to: /home/nikita/Nikita0042/workspace/projects/lab03/hello_world_application/_build
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/	hello_world_application$ cmake --build _build
	Consolidate compiler generated dependencies of target formatter
	[ 16%] Building CXX object /home/nikita/Nikita0042/workspace/projects/lab03/formatter_lib/_build/CMakeFiles/formatter.dir/formatter.cpp.o
	[ 33%] Linking CXX static library libformatter.a
	[ 33%] Built target formatter
	Consolidate compiler generated dependencies of target formatter_ex
	[ 50%] Building CXX object /home/nikita/Nikita0042/workspace/projects/lab03/formatter_ex_lib/_build/CMakeFiles/formatter_ex.dir/formatter_ex.cpp.o
	[ 66%] Linking CXX static library libformatter_ex.a
	[ 66%] Built target formatter_ex
	Consolidate compiler generated dependencies of target hello_world
	[ 83%] Linking CXX executable hello_world
	[100%] Built target hello_world
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/hello_world_application$ cd ..
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03$ cd solver_lib
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/solver_lib$ nano CMakeLists.txt
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/solver_lib$ cmake -H. -B_build
	-- The C compiler identification is GNU 9.3.0
	-- The CXX compiler identification is GNU 9.3.0
	-- Detecting C compiler ABI info
	-- Detecting C compiler ABI info - done
	-- Check for working C compiler: /usr/bin/cc - skipped
	-- Detecting C compile features
	-- Detecting C compile features - done
	-- Detecting CXX compiler ABI info
	-- Detecting CXX compiler ABI info - done
	-- Check for working CXX compiler: /usr/bin/c++ - skipped
	-- Detecting CXX compile features
	-- Detecting CXX compile features - done
	-- Configuring done
	-- Generating done
	-- Build files have been written to: /home/nikita/Nikita0042/workspace/projects/lab03/solver_lib/_build
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/solver_lib$ cmake --build _build
	Consolidate compiler generated dependencies of target solver_lib
	[ 50%] Building CXX object CMakeFiles/solver_lib.dir/solver.cpp.o
	/home/nikita/Nikita0042/workspace/projects/lab03/solver_lib/solver.cpp: In function ‘void solve(float, float, float, float&, float&)’:
	/home/nikita/Nikita0042/workspace/projects/lab03/solver_lib/solver.cpp:	14:21: error: ‘sqrtf’ is not a member of ‘std’
	   14 |     x1 = (-b - std::sqrtf(d)) / (2 * a);
	      |                     ^~~~~
	/home/nikita/Nikita0042/workspace/projects/lab03/solver_lib/solver.cpp:	15:21: error: ‘sqrtf’ is not a member of ‘std’
	   15 |     x2 = (-b + std::sqrtf(d)) / (2 * a);
	      |                     ^~~~~
	make[2]: *** [CMakeFiles/solver_lib.dir/build.make:76: CMakeFiles/solver_lib.dir/solver.cpp.o] Ошибка 1
	make[1]: *** [CMakeFiles/Makefile2:83: CMakeFiles/solver_lib.dir/all] 	Ошибка 2
	make: *** [Makefile:91: all] Ошибка 2
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/solver_lib$ nano solver.cpp
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/solver_lib$ cmake -H. -B_build
	-- Configuring done
	-- Generating done
	-- Build files have been written to: /home/nikita/Nikita0042/workspace/projects/lab03/solver_lib/_build
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/solver_lib$ cmake --build _build
	Consolidate compiler generated dependencies of target solver_lib
	[ 50%] Building CXX object CMakeFiles/solver_lib.dir/solver.cpp.o
	[100%] Linking CXX static library libsolver_lib.a
	[100%] Built target solver_lib
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/solver_lib$ cd ..
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03$ cd solver_application
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/solver_application$ nano CMakeLists.txt
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/solver_application$ cmake -H. -B_build
	-- Configuring done
	-- Generating done
	-- Build files have been written to: /home/nikita/Nikita0042/workspace/projects/lab03/solver_application/_build
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/solver_application$ cmake --build _build
	Consolidate compiler generated dependencies of target solver_lib
	[ 12%] Building CXX object /home/nikita/Nikita0042/workspace/projects/lab03/solver_lib/_build/CMakeFiles/solver_lib.dir/solver.cpp.o
	[ 25%] Linking CXX static library libsolver_lib.a
	[ 25%] Built target solver_lib
	Consolidate compiler generated dependencies of target formatter
	[ 37%] Building CXX object /home/nikita/Nikita0042/workspace/projects/lab03/formatter_lib/_build/CMakeFiles/formatter.dir/formatter.cpp.o
	[ 50%] Linking CXX static library libformatter.a
	[ 50%] Built target formatter
	Consolidate compiler generated dependencies of target formatter_ex
	[ 62%] Building CXX object /home/nikita/Nikita0042/workspace/projects/lab03/formatter_ex_lib/_build/CMakeFiles/formatter_ex.dir/formatter_ex.cpp.o
	[ 75%] Linking CXX static library libformatter_ex.a
	[ 75%] Built target formatter_ex
	Consolidate compiler generated dependencies of target solver
	[ 87%] Linking CXX executable solver
	[100%] Built target solver
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/solver_application$ 
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/solver_application$ ./_build/solver
	1
	0
	-4
	-------------------------
	x1 = -2.000000
	-------------------------
	-------------------------
	x2 = 2.000000
	-------------------------
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/solver_application$ cd ..
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03$ cd hello_world_application
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/hello_world_application$ ./_build/hello_world
	-------------------------
	hello, world!
	-------------------------
######	nikita@nikita-VirtualBox:~/Nikita0042/workspace/projects/lab03/hello_world_application$ 
