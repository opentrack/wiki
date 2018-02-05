Here are some pointers on how to build opentrack as Jul 8, 2016 with point tracker support under VC++.

## Caveats

Versions older than Visual C++ 2017 Preview won't work since they don't support modern C++ features. After a new Visual Studio release, there won't be a Preview requirement.

Look at [Microsoft's conformance status](https://docs.microsoft.com/en-us/cpp/visual-cpp-language-conformance) to see if the release version has caught up with Preview.

## Requirements
- At least Visual C++ 2017 Preview.
- [CMake](https://cmake.org/downloads/)
- [Qt 5.10](https://download.qt.io/archive/qt/5.10/) is required for latest code build
- OpenCV 3.0 or OpenCV [master branch](https://github.com/opencv/opencv/)
- (git)

These are optional but highly recommended. Instructions assume they're installed and placed somewhere in user's `PATH`.

- [Ninja](https://github.com/ninja-build/ninja)
- [Jom](https://wiki.qt.io/Jom)

## Building
It is assumed that we are building a 32-bit version. Generally, we must use the same kind of binary, i.e. either 64-bits or 32-bits for all libraries that will be linked and of course for the opentrack application itself.

### Installing Qt built with MSVC++ 17 Preview

Use the .zip file from `http://download.qt.io/` then run `configure.bat`. You need to install Qt into your selected prefix, then specify Qt_DIR as `Z:/some/qt/prefix/lib/cmake/Qt5` to detect the modules.

First edit `qtbase/mkspecs/common/msvc-desktop.conf` and replace **all occurences** of `-MD` or `/MD` with `-MT`.

When using `jom` as the make tool, it helps adding `-cgthreads:1` to `QMAKE_LFGLAGS` and `-cgthreads1` to `QMAKE_CXXFLAGS`.

There's no typo in the previous paragraph, that's the idiosyncratic syntax for MSVC. See MSDN documentation for these options for an explanation of the options, and think carefully how it interacts with a `jom` multicore build.

Recommended flags to `configure.bat`:

```
-shared -opensource -confirm-license -release
-no-rtti
-prefix D:/dev/qt-msvc15-5.7.0 ← (here pass your own favorite prefix)
-platform win32-msvc
-opengl desktop -no-angle
-no-compile-examples
-make-tool jom
-no-mp ← (only with jom)
-no-harfbuzz -no-fontconfig -no-freetype
-force-debug-info
```

### Partial Qt build

In fact we only need to compile few individual Qt components. Rather than downloading the whole package, go to the `submodules/` directory on the download site. Download and compile only `qtbase`, `qttools`, and `qtserialport`, in that order. Building the entirety of Qt takes a long time and is a waste.

The last two you build by invoking `qmake.exe` from `qtbase` you installed, only then run `nmake` or `jom`.

### Installing OpenCV

OpenCV does not come in binary releases that link against the 2015 runtime of VC as of today. Hence we need to build it from sources. 

You can follow the instructions on the OpenCV project site http://docs.opencv.org/2.4/doc/tutorials/introduction/windows_install/windows_install.html

We want to generate an MSVC-built project using `cmake`, or rather `cmake-gui` which is easier. The following steps should make it work:
- Select `Show advanced` and `Grouped` in `cmake-gui` to the right side of the build directory selection.
- First CMake will prompt to select the build system. We use the `VC++ 2017 64-bit` variant which might well be the default.
- Add `/DHAVE_DSHOW` to `CMAKE_CXX_FLAGS`. This is required to enable building of direct show video capture support. There are other ways to enable video capture, depending on the operating system and software you might have installed. Here it is assumed that we build under Windows 7 64-bit.
- Change some build options:
    1. Disable BUILD_SHARED_LIBS (opentrack-track-pt is designed to statically link with OpenCV lib.)
    1. Enable BUILD_WITH_STATIC_CRT
    1. Enable BUILD_WITH_DEBUG_INFO
- Run the `build` target. There's no need to run the `install` target.

### Building opentrack
It is assumed that we have the opentrack sources in `D:\Dev\opentrack` and have a out-of-source build directory in `D:/Dev/opentrack/build`. It does not really matter but we don't want to install our build products into the source dir. 

Before building, read this document's latter sections.

Just like OpenCV, we use CMake to create a VC project for opentrack. Some configuration steps are required:
- Set the install dir `CMAKE_INSTALL_PREFIX` to anything suiteable, e.g. `D:/Dev/opentrack/build/install`.
- Set the search path for Qt. It should point to the directory where Qt CMake files are located. In our case `Qt5_DIR=D:/Dev/Qt/5.7/msvc2015_64/lib/cmake/Qt5`
- Set the search path to opencv's build directory. `OpenCV_DIR=D:/Dev/opencv/build`.
Then generate the project file and hopefully build cleanly in VC++. Build the `INSTALL` target.

### CMake Toolchain file

You may use our toolchain file as `cmake -DCMAKE_TOOLCHAIN_FILE=/path/to/opentrack/cmake/msvc.cmake src-path` when first initializing a build directory, if you find it to your liking. It'll set up some common compiler flags opentrack for aggressive optimizations, fast `LTCG` link time, and generating debug info.

### More opentrack modules

We are still missing other optional dependencies. Required dependencies for a complete build can be found in `https://github.com/opentrack/opentrack-depends`. Remember to use `--recurse-submodules` when cloning or update git submodules later.

#### Windows XP support

opentrack doesn't support Windows XP anymore due to Qt 5.10 requirement. 5.6 was the last version supporting XP.

You may attempt changing opentrack's sources to build with Qt 5.6 but the maintainer has given up due to ever-shrinking Windows XP user base. In any case build with `-MT` under all circumstances when targetting XP to save a major headache when deploying on XP machines.

## Troubleshooting
In case opentrack crashes on start of point tracker, it might be that the OpenCV build was actually compiled without video capture support. Watch opentrack's console output. If you launch `opentrack.exe` from the Command Prompt, it'll spew debug data on its screen, regardless of any build flags.

## The instructions are likely incomplete

The instructions won't work step-by-step and haven't been reproduced from scratch. You'll run into unexpected problems along the way and rudimentary build system knowledge is necessary.

Some of Qt-related build errors are strange and hard to diagnose. Google for them, diagnosing on one's own is hardly possible not being a Qt developer.

When building things, find `Developer Command Prompt for VS 2017 Preview` in the Start Menu and use that console rather than the empty Command Prompt environment. Again, make sure `jom` and `ninja` are in system `PATH`.

Use `NMake` or `Jom` when building Qt. Use Ninja as `Generator` when generating CMake projects. `cmake-gui` prompts for selection when first generating the project.