Opentrack does not provide binaries for Linux users. The following is a brief attempt at the missing guide on compiling Opentrack for Linux.

## Building on Debian, Ubuntu, etc.

## 1. Install Dependencies

The following dependencies are required in order to build Opentrack. First:

```sh
sudo apt update
```

Then:

### On Debian/Ubuntu:

```sh
sudo apt install build-essential cmake git libopencv-dev libproc2-dev qt6-base-private-dev qt6-tools-dev
```

### On Manjaro

```sh
sudo pacman -S cmake git opencv procps-ng qt5-base qt5-tools
```

### On Fedora:

```sh
dnf install cmake git opencv-devel procps-ng-devel qt6-qtbase-private-devel qt6-qttools-devel
```

---

Users of other distributions are encouraged to expand upon this guide.

While Opentrack will compile without OpenCV, only a very minimal subset of functionality will be available, making it of little use to the average user. 

## 2. Clone the source

```bash
git clone https://github.com/opentrack/opentrack
cd opentrack/
```

## 3. Configure

Set configuration options, as for any cmake project. To run Opentrack on
Linux, you'll probably want to set `SDK_WINE=ON`, i.e:

```sh
cmake . -DSDK_WINE:BOOL=ON
```

Alternatively, use '`ccmake .`' to view an interactive list of available configuration variables. When done, press `c` to reconfigure, `e` to dismiss the resulting dialog, and then `g` to generate the configuration.

> For me on Ubuntu 25.04, including the SDL_WINE=ON config causes the subsequent
> compile step to fail with an error about linking to 32-bit libraries. I'll add
> any required fixes here when I figure that out. If it works fine for you,
> delete this para, thanks!

## 4. Compile

```sh
make -j$(nprocs)
```

The `-j` arg does the compilation in parallel across all your CPUs, so speeds
things up tremendously. I see anecdotal reports on Reddit that using this
option caused problems for some people, so if you get errors, it might be worth
trying again using plain `make` with no args, although I find this hard to
credit, personally -- using `make -j...` is a very common thing to do.

## 5. Install the compiled program

```sh
make -j$(nprocs) install
```

This installs to wherever the config variable `CMAKE_INSTALL_PREFIX` points to,
by default just `./install`.

## 6. Run your compiled Opentrack

Change to the install's bin directory and try it out:

```
cd install/bin
./opentrack
```

## 7. Variations

You might want to change the directory we install Opentrack to, in which case
modify the `CMAKE_INSTALL_PREFIX` configuration, e.g:

```sh
cmake . -DSDK_WINE:BOOL=ON -DCMAKE_INSTALL_PREFIX:PATH=$HOME/.local
```

and then recompile, etc.

