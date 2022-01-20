

# Introduction
We are glad you are enjoying opentrack and want to contribute. Here is something to get you started ASAP.

# Purpose and scope
This document is intended for Software Engineer, assuming C++ skills and CMake experience. 
It should help you build our project and develop for opentrack.
Things like building your own Qt5 and OpenCV builds is outside the scope of this document.

# Development platform
Most of the development is happening on Microsoft Windows using Visual Studio 2017 Community Edition.
But this guide we will be using Msys2 & MinGw.
VS a big bloat for many people and isnt the tool to use for software that is opensource & crossplatform :D
We have perfectly good crossplatform toolchain. in terms of: msys2, mingw, +the build tools such as make etc.
This should be the standard for crossplatform projects, but i digress.

# Supported platform for Opentrack.
Microsoft Windows 7 to 10, Linux. Apple's OSX has not been properly tested in a while.

# Supported architecture
Though official releases are still 32-bit only, 64-bit builds are working great too.

# Programming language
Most of opentrack is implemented using C++17.

#  Build prerequisite
* **MSYS2**. get it from [here](https://www.msys2.org/) or [here](https://github.com/msys2/msys2-installer/releases).
* If fresh install of MSYS, you should probably run: pacman -Syu followed by pacman -Su ,check MSYS'2 Documentation on updating.
* pacman will deal with the dependencies so they are not listed her as it would be to much.

# Build instructions
* The MSYS2 packages can be found by using (pacman -Ss name) or here: https://packages.msys2.org/queue 
* We will start of by getting the tools needed. Open the MSYS2 MinGW 64-bit console. 
    * **pacman -S mingw-w64-x86_64-gcc**    - The GNU Compiler Collection (C,C++,OpenMP) for MinGW-w64
    * **pacman -S mingw-w64-x86_64-make**   - The GNU make utility to maintain groups of programs.
    * **pacman -S mingw-w64-x86_64-cmake**  - A cross-platform open-source make system.
    * **pacman -S mingw-w64-x86_64-qt5**    - Meta package for Qt5 components (mingw-w64)
	* **pacman -S mingw-w64-x86_64-opencv** - OpenCV is optionally.
	* Im not sure if i have forgotten anything, it's been a while since i have installed my toolchain. And i have installed a bunch of tools for other projects. ie. autoconf etc. So there is a chance that something is missing.

* Next setup|check the system variables and make sure atleast these paths are added to the system PATH.
	* **x:\Path_to_msys\usr\bin**
	* **x:\Path_to_msys\usr\include**
	* **x:\Path_to_msys\mingw64\include**
	* **x:\Path_to_msys\mingw64\lib**
	* **x:\Path_to_msys\mingw64\bin**

* Now the tools and libs are downloaded and installed we are are ready to start.
	* Open a new cmd.exe so it has the newly added system variables. (if all is setup correctly you can close the msys console)
	* The location for our project will be in **<X:\dev>** So, cd into that. You replace <X:\dev> with whatever your path is. 
		* <X:\dev>
	* **git clone https://github.com/opentrack/opentrack.git** - Get the source code for Opentrack from github. (you dont have to use git, but why not.)
	* cd into opentrack and run (git pull --rebase) just to check all is ok and up to date. 
		* **<X:\dev\opentrack>git pull --rebase**
	* **mkdir build && cd build** - Creates the build directory and cd into it.
		* <x:\dev\opentrack\build>
	* Run cmake to generate our Makefile(s)
		* **<x:\dev\opentrack\build>cmake -G"MSYS Makefiles" -B . -S ../ -DCMAKE_TOOLCHAIN_FILE=../cmake/mingw-w64.cmake**
	* Finally we can run make, it will take a few min, go get some coffee :).
		* **<x:\dev\opentrack\build>make && make install**
	* When make and make install is done the program can be found at.
		* **<X:\dev\opentrack\install>**


# Note
 * Not all plugins/modules will be compiled. Example the tracker-neuralnet, it requires a bit more work.
