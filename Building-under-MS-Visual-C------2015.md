Here are some pointers on how to build opentrack as Jul 8, 2016 with point tracker support under VC++.

## Caveats

Versions older than Visual C++ 2015 won't work since they don't support modern C++ features.

## Requirements
- At least Visual C++ 2015. Visual Studio 15 Preview will also work and produce higher-quality code.
- [CMake](https://cmake.org/files/v3.8/cmake-3.8.0-rc2-win64-x64.zip)
- [Qt5](http://download.qt.io/archive/qt/5.7/5.7.0/qt-opensource-windows-x86-msvc2015_64-5.7.0.exe)
- OpenCV 3.0
- (git)

## Building
It is assumed that we are building a 64-bit version. Generally, we must use the same kind of binary, i.e. either 64-bits or 32-bits for all libraries that will be linked and of course for the opentrack application itself.

### Installing Qt

#### For MSVC++ 2015

We use the Qt online installer. Go to the Qt download page select the open source version. Eventually you will get to download the installer named qt-unified-windows-x64-2.03-online.exe or something similar.

Start the install. We only need the `mscvc2015_64` components. Still it is going to be a large download of ca. 1 GB. It is assumed that the top level install dir is `D:\Dev\Qt`. The libs that we are interested in will be thus located in
```
D:\Dev\Qt\5.7\msvc2015_64\lib
D:\Dev\Qt\5.7\msvc2015_64\bin
```
or similar, depending on your version of Qt.

#### For MSVC++ 15 Preview

Use the .zip file from `http://download.qt.io/`, then you can run `configure.bat`. You need to install Qt into a prefix, then specify Qt_DIR as `/some/qt/prefix/lib/cmake/Qt5` to detect the modules.

Recommended flags to `configure.bat`:

```
-shared
-opensource
-confirm-license
-release
-prefix
D:/dev/qt-msvc15-5.7.0 ← (here pass your own favorite prefix)
-ltcg
-platform
win32-msvc2015
-opengl
desktop
-no-rtti
-target
xp
-no-compile-examples
```

### Installing OpenCV
OpenCV does not come in binary releases that link against the 2015 runtime of VC as of today. Hence we need to build it from sources. 

You can follow the instructions on the OpenCV project site http://docs.opencv.org/2.4/doc/tutorials/introduction/windows_install/windows_install.html

It's recommended to build opentrack's custom version of opencv along with other SDKs.

```
git clone --recurse-submodules https://github.com/opentrack/opentrack-depends.git
```

You may also only clone opentrack's fork of opencv.

```
git clone https://github.com/opentrack/opencv opencv-source
```

However, it'll still work with the original version

```
git clone https://github.com/opencv/opencv.git opencv-source
```

We want to generate a MSVC project using `cmake`, or rather `cmake-gui` which is easier. The following steps should make it work:
- First CMake will prompt to select the build system. We use the `VC++ 2015 64-bit` variant which might well be the default.
- Add `/DHAVE_DSHOW` to `CMAKE_CXX_FLAGS`. This is required to enable building of direct show video capture support. There are other ways to enable video capture, depending on the operating system and software you might have installed. Here it is assumed that we build under Windows 7 64-bit.
- Disable dependencies that are not available.
 1. BUILD_opencv_python2
 1. WITH_CUDA
- Set `CMAKE_INSTALL_PREFIX` to your desired destination directory. `D:\Dev\opencv` is assumed.
Then generate the configuration, launch VC++ and hopefully build cleanly. Run the `INSTALL` build target if it does not automatically do so.

### Building opentrack
It is assumed that we have the opentrack sources in `D:\Dev\opentrack-source` and have a out-of-source build directory in `D:\Dev\opentrack-build`. It does not really matter but we don't want to install our build products into the source dir. 

Just like OpenCV, we use CMake to create a VC project for opentrack. Some configuration steps are required:
- Set the install dir `CMAKE_INSTALL_PREFIX` to anything suiteable, e.g. `D:\Dev\opentrack`.
- Set the search path for Qt. It should point to the directory where Qt CMake files are located. In our case `Qt5_DIR=D:/Dev/Qt/5.7/msvc2015_64/lib/cmake/Qt5`
- Set the search path for OpenCV. `OpenCV_DIR=D:\Dev\opencv`.
Then generate the project file and hopefully build cleanly in VC++. Build the `INSTALL` project.

We still need to ensure that the dependency libraries are found. To do so, either change your `PATH` variable to point to `D:\Dev\Qt\5.7\msvc2015_64\bin` and `D:\Dev\opencv\x64\vc14\bin`. Or copy various dll's directly into your opentrack install dir.

As previously mentioned, we are still missing other optional dependencies. Required dependencies for a complete build can be found in `https://github.com/opentrack/opentrack-depends`. Remember to use `--recurse-submodules` when cloning or update git submodules later.

### Toolchain file

You may use our toolchain file as `cmake -DCMAKE_TOOLCHAIN_FILE=/path/to/opentrack/cmake/msvc.cmake src-path` when first initializing a build directory, if you find it to your liking. It'll set up some common compiler flags including install directory for opentrack.

### Windows XP support for resulting binaries.

In short, you need to build everything with the `/MT` flag, replacing `/MD`, including building Qt from source.

```
QMAKE_CFLAGS            = -nologo -Zc:wchar_t /MT
```

## Troubleshooting
In case opentrack crashes on start of point tracker, it might be that the OpenCV build was actually compiled without video capture support. 

Set the `SDK_CONSOLE_DEBUG` cache variable to have a console window in addition to the program's main window. Of course an actual debugger may be necessary.