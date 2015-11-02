## General

Qt 5.x won't build on Cygwin as <code>qmake</code> doesn't build there. It needs to run on the build triple, not merely on the target.

Use instead the official [mingw-w64 installer](https://sourceforge.net/projects/mingw-w64/) and adjust path in `cmake/mingw-w64.cmake` to point to this one. Recommend not using spaces in installation directory.

You could use Cygwin's mingw-w64 cross-compiler but it interfaces poorly with Qt Creator and is outdated.

## Qt5

Don't use prebuild Qt5 binaries as they have a different ABI than the used cross-compiler. opentrack crashing on startup isn't a bug in this configuration.

A good way to build Qt from mingw-w64 shell is
<pre>
mkdir build
cd build
sh ../configure -platform win32-g++ -shared -release -opensource -confirm-license -prefix c:/wherever/qt-win32-5.whatnot -xplatform win32-g++
</pre>

Build and install with
<pre>
sh -c 'make module-{qtbase,qtserialport}-{all,install_subtargets}'
</pre>

Additionally you can interrupt the build and replace `examples/` and `tests/` subdirectories after they get created with the following
<pre>
all::
install::
</pre>
to prevent build errors and build time being too long.

Additionally, you can replace a declaration in `qtbase/mkspecs/win32-g++/qmake.conf` with the following:

<pre>
CONFIG                 += release release_target precompile_header
</pre>

prior to configuring, as to prevent debug libraries from building thus increasing build time.

Copy `libgcc` and `libstdc++` .dll's to `Qt-prefix/bin`.

## Building opentrack

Use the toolchain file as per
<pre>
mkdir build
cd build
cmake -D CMAKE_TOOLCHAIN_FILE=$(pwd)/../cmake/mingw-w64.cmake ..
</pre>

to ease cross-compiler usage.

Compile opentrack-depends.

Run `cmake-gui` on opentrack and specify depends' paths.

Copy Qt .dlls and plugins/platforms/qwindows.dll to the install prefix. Look up a binary release for the correct layout.

If OpenCV is build dynamically, copy their .dll's appropriately.

Specify install prefix, install. Optionally run InoSetup. You may need to adjust paths.

Please distinguish the releases from official project releases.