Opentrack does not provide binaries for Linux users. The following is a brief attempt at the missing guide on compiling Opentrack for Linux.

## Building on Debian, Ubuntu, etc.

## 1. Install Dependencies

The following dependencies are required in order to build Opentrack. First:

```sh
sudo apt update
```

Then:

### On Debian/Ubuntu

```sh
sudo apt install build-essential cmake git libopencv-dev libproc2-dev qt6-base-private-dev qt6-tools-dev wine64-tools
```

### On Arch/Manjaro

```sh
sudo pacman -S cmake git opencv procps-ng qt6-base qt6-tools
```

### On Fedora

```sh
sudo dnf install cmake git opencv-devel procps-ng-devel qt6-qtbase-private-devel qt6-qttools-devel
```

Users of other distributions are encouraged to expand upon this guide.

## 2. Optional dependencies

You'll also need to install the following optional dependencies:

| Debian/Ubuntu  | Arch/Manjaro | Fedora     | Description                                           |
| -------------- | ------------ | ---------- | ----------------------------------------------------- |
| `wine64-tools` | ???          | wine-devel | Needed to set SDK_WINE=ON config, as described below. |

(i.e. repeat the apt/pacman/dnf command from above, with the optional dependencies
you need appended to the end.)

## 3. Clone the source

```bash
git clone https://github.com/opentrack/opentrack
cd opentrack/
```

## 4. Configure

Set configuration options, as for any cmake project. To run Opentrack on
Linux, you'll probably want to set `SDK_WINE=ON`, i.e:

```sh
cmake . -DSDK_WINE:BOOL=ON
```

Alternatively, use '`ccmake .`' to view an interactive list of available configuration variables. When done, press `c` to reconfigure, `e` to dismiss the resulting dialog, and then `g` to generate the configuration.

## 5. Compile

```sh
make -j$(nproc)
```

The `-j` arg does the compilation in parallel across all your CPUs, so speeds
things up tremendously.

## 6. Install

```sh
make -j$(nproc) install
```

This installs to wherever the config variable `CMAKE_INSTALL_PREFIX` points to,
by default just `./install`.

## 7. Run

Change to the install's bin directory and try it out:

```sh
cd install/bin
./opentrack
```

## 8. Variations

You might want to change the directory we install Opentrack to, in which case
modify the `CMAKE_INSTALL_PREFIX` configuration, e.g:

```sh
cmake . -DSDK_WINE:BOOL=ON -DCMAKE_INSTALL_PREFIX:PATH=$HOME/.local
```

and then recompile, etc.
