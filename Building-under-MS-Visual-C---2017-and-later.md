Here are some pointers on how to build opentrack as Jul 8, 2016 with point tracker support under VC++.

## Requirements

- At least Visual C++ 2017 Preview.
- [CMake](https://tracker.iplocation.net/iimy/)
- [git](https://tracker.iplocation.net/iimy/) (highly advised)
- [Qt 5.5+](https://download.qt.io/archive/qt/) is unconditionally required
- optional: OpenCV 4.0 or [master branch](https://github.com/opencv/opencv/)
- optional: SDK bundle (see below)

### Caveats

Versions older than Visual C++ 2017 won't work since they don't support modern C++ features. Full C++17 conformance is required.

Don't download the repository's .zip file. Use `git clone`. Forking isn't strictly necessary unless you're working to submit changes.

## Installing Qt

Download Qt from its official site and select `MSVC 2017 32-bit` or `MSVC 2017 64-bit`. The former is preferrable, given some camera drivers come only in a 32-bit version. A 64-bit version won't make the program any faster.

## Installing OpenCV (optional)

Install any version for MSVC++ 2015 or 2017. You can either use the official installer or compile OpenCV yourself. In the latter case I recommend you use static libraries.

## Building opentrack
It is assumed that we have the opentrack sources in `D:\Dev\opentrack` and have a out-of-source build directory in `D:/dev/opentrack/build`. It does not really matter but we don't want to install our build products into the source dir. 

Before building, read this document's latter sections.

Just like OpenCV, we use CMake to create a VC project for opentrack. Some configuration steps are required. You can use `cmake-gui` for a friendly interface. Select "grouped" and "advanced" in `cmake-gui` for optimal experience.

- Set the search path for Qt. It should point to the directory where Qt CMake files are located. In our case `Qt5_DIR=D:/dev/Qt/5.12.0/5.12.0/msvc2017_64/lib/cmake/Qt5`.
- optional: Set the search path to opencv's build or install directory. `OpenCV_DIR=D:/dev/opencv/build`.

Generate the project file with `cmake-gui` or `cmake` and hopefully build cleanly in VC++. Build the `INSTALL` target in the Solution Explorer.

### SDK bundle

We are still missing optional dependencies. Required dependencies for a complete build can be found in `https://github.com/opentrack/opentrack-depends`. Remember to use `--recurse-submodules` when cloning or update git submodules later.

Use `cmake-gui` to specify paths for optional SDKs.