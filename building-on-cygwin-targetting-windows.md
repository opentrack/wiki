Qt 5.x won't build on Cygwin as <code>qmake</code> doesn't build there.

Use instead the official [mingw-w64 installer](https://sourceforge.net/projects/mingw-w64/) and adjust path in `cmake/mingw-w64.cmake` to point to this one. Recommend not using spaces in installation directory.

You could use Cygwin's mingw-w64 cross-compiler but it interfaces poorly with Qt Creator and is outdated.

Copy `libgcc` and `libstdc++` .dll's to Qt-prefix/bin.

Use toolchain file as per
> cmake -D CMAKE_TOOLCHAIN_FILE=$(pwd)/../cmake/mingw-w64.cmake ..</code>

to ease cross-compiler usage.

Compile opentrack-depends.

Run `cmake-gui` on opentrack and specify depends' paths.

Copy Qt .dlls and plugins/platforms/qwindows.dll to the install prefix. Look up a binary release for the correct layout.

If OpenCV is build dynamically, copy their .dll's appropriately.

Specify install prefix, install. Optionally run InoSetup. You may need to adjust paths.

Please distinguish the releases from official project releases.