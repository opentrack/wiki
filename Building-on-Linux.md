Opentrack does not provide binaries for Linux users. The following is a brief attempt at the missing guide on compiling Opentrack for Linux. Users of other distributions are encouraged to submit PRs improving this document.

## 1. Install Dependencies

The following dependencies are required to build Opentrack.

### On Debian/Ubuntu

```sh
sudo apt update
sudo apt install build-essential cmake git libopencv-dev libproc2-dev qt6-base-private-dev qt6-tools-dev
```

### On Arch/Manjaro

```sh
sudo pacman -S cmake git opencv procps-ng qt6-base qt6-tools
```

### On Fedora

```sh
sudo dnf install cmake git opencv-devel procps-ng-devel qt6-qtbase-private-devel qt6-qttools-devel
```

## 2. Clone the source

```bash
git clone https://github.com/opentrack/opentrack
cd opentrack/
```

## 3. Configure

Set configuration options, as for any cmake project:

### 3a. Interactively

Available config variables can be viewed and edited interactively, with:

```sh
cmake -B build
ccmake build
```

(The 'build' directory this generates can be called anything, so you can manage multiple builds, perhaps using different configuration values.)

When done, press `c` to reconfigure, `e` to dismiss the resulting dialog, and then `g` to generate the configuration.

The defaults values should be fine for now.

### 3b. From the command-line

Alternatively, configuration can be set at the command line, using `-D` to define the value of each variable, eg:

```sh
cmake -B build -DSDK_WINE=ON
```

## 4. Optional dependencies

Use the table below to see if you'll need any optional dependencies. If you do, then repeat the above apt/pacman/dnf command, with the optional dependencies appended to the end.

Similarly, some of the following functionalities require you to set more config variables. Run 'the 'cmake' or 'ccmake' commands above to set any extra configuration variables you need.

The table shows dependencies for particular distros. PRs to cater to other distros are welcome.

Functionality | Debian | Fedora | Config variables
-|-|-
Aruco paper marker tracker | `libopencv-dev`,<br />compile `libaruco` (see below) | | `SDK_ARUCO_LIBPATH=<path>`
EasyTracker | `libopencv-dev` | | 
FTNoIR PointTracker | `libopencv-dev` | |
Hatire head tracker | `qt6-serialport-dev`<br />(was `libqt5serialport5-dev`) | |
Intel RealSense | `librealsense2-dev` ([docs](https://github.com/IntelRealSense/librealsense/blob/master/doc/distribution_linux.md)) | | `SDK_REALSENSE=<path>`<br />(or env var `RSSDK_DIR`)
libevdev ([docs](https://www.freedesktop.org/wiki/Software/libevdev/)) | `libevdev-dev` | |
NeuralNet tracker with ONXX | `libopencv-dev`,<br />Download and extract<br />[onxx tarball](https://github.com/microsoft/onnxruntime/releases) | | `ONNXRuntime_DIR=<path>`<br />and env var `ONXXRuntime_ROOT`<br />to same path.
Oscpack | `liboscpack-dev` | | `SDK_OSCPACK=/usr`
Valve SteamVR support | Download and extract<br />[Valve SteamVR SDK](https://github.com/ValveSoftware/openvr) | | `SDK_VALVE_STEAMVR=<path>`
Wine/Proton | `wine64-tools` | `wine-devel` | Needed to set `SDK_WINE=ON`, as described below.
X-Plane | Download and extract<br />[X-Plane Plugin SDK](https://developer.x-plane.com/sdk/plugin-sdk-downloads/) | | `SDK_XPLANE=<path>`

### libaruco

Needed for Aruco paper marker tracker, but you'll have to compile it yourself. In a new directory:

```sh
git clone https://github.com/opentrack/aruco.git
cd aruco
cmake -B build -DCMAKE_BUILD_TYPE=RELEASE
cmake --build build
```

Then specify the full path of `aruco/build/src/` using the config variable `SDK_ARUCO_LIBPATH`.

## 5. Compile

```sh
(cd build; make -j$(nproc))
```

The `-j` arg does the compilation in parallel across all your CPUs, so speeds things up tremendously.

## 6. Install

```sh
(cd build; make -j$(nproc) install)
```

This installs to wherever the config variable `CMAKE_INSTALL_PREFIX` points to, which defaults to `./build/install`.

## 7. Run

Run the installed executable to try it out, e.g.:

```sh
cd build/install/bin
./opentrack
```

## 8. Variations

You might want to change the directory we install Opentrack to, in which case
modify the `CMAKE_INSTALL_PREFIX` configuration, e.g:

```sh
cmake . -DSDK_WINE:BOOL=ON -DCMAKE_INSTALL_PREFIX:PATH=$HOME/.local
```

and then recompile, etc.
