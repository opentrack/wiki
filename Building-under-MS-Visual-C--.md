Here are some pointers on how to build opentrack as Jul 8, 2016 with point tracker support under VC++.
## Requirements
- Visual C++ 2015. Earlier versions lack the required C++11 support. You can use the Visual Studio Community Edition which is free.
- CMake
- Qt5
- OpenCV 3.0

## Building
It is assumed that we are building a 64-bit version. Generally, we must use the same kind of binary, i.e. either 64-bits or 32-bits for all libraries that will be linked and of course for the opentrack application itself.

### Installing Qt
We use the Qt online installer. Go to the Qt download page select the open source version. Eventually you will get to download the installer named qt-unified-windows-x64-2.03-online.exe or something similar.

Start the install. We only need the `mscvc2015_64` components. Still it is going to be a large download of ca. 1 GB. It is assumed that the top level install dir is `D:\Dev\Qt`. The import libs we are interested in are thus in 
```
D:\Dev\Qt\5.7\msvc2015_64\lib
```
or similar, depending on your version of Qt.


