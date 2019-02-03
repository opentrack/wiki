# Introduction
We are glad you are enjoying opentrack and want to contribute. Here is something to get you started ASAP.

# Purpose and scope
This document is intended for Software Engineer, assuming C++ skills and CMake experience. It should help you build our project and develop for openstack.

# Development platform
Most of the development is happening on Microsoft Windows using Visual Studio 2017 Community Edition.
Though I guess you could develop on Linux or OSX this guide will be assuming Windows as it is surely the easiest and fastest way to get started with opentrack.

# Supported platform
Microsoft Windows 7 to 10, Linux. Apple's OSX as not been properly tested in a while.

# Supported architecture
Though official releases are still 32-bit only, 64-bit builds are working great too.

# Programming language
Most of opentrack is implemented using C++17.

#  Build prerequisite
* Microsoft Windows 7 to 10.
* [Visual Studio 2017 Community Edition](https://visualstudio.microsoft.com/downloads/).
* [CMake > 3.10](https://cmake.org/download/).
* [Qt5 SDK > 5.12.0](https://www.qt.io/download-qt-installer), we recommend using the online installer.

# Optional build dependencies
* [OpenCV > 4.0.1](https://opencv.org/releases.html) - 64-bit binaries only: Needed to build popular modules such as Point Tracker.

# Build instructions
* Use CMake application to configure opentrack and generate the Visual Studio solution.
    * Select Visual Studio 15 2017 generator. Choose the Win64 variant if you need to use OpenCV.
    * Provide Qt5_DIR cache variable. It should look like: `C:\Dev\Qt\5.12.0\msvc2017_64\lib\cmake\Qt5`.
    * Optionally provide OpenCV_DIR cache variable. It should look like: `D:\Dev\OpenCV\4.0.1\build\x64\vc15\lib`.
* Generate and open your project solution.
* Select `RelWithDebInfo` target as the default `Debug` target is known to cause problems.
* Build your solution.
* Build the `INSTALL` project.
* If using OpenCV copy its DLLs into the `modules` folder.
* You should now be able to run and debug `opentrack.exe` from the CMake install folder.

Alternatively you could also do your own Qt5 and OpenCV builds, that's however outside the scope of this document. 