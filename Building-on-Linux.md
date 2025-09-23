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
sudo apt install build-essential cmake git libopencv-dev libproc2-dev qt6-base-private-dev qt6-tools-dev wine64-tools
```

### On Arch/Manjaro

```sh
sudo pacman -S cmake git opencv procps-ng qt6-base qt6-tools
```

### On Fedora:

```sh
dnf install cmake git opencv-devel procps-ng-devel qt5-linguist qt5-qtbase-private-devel qt6-qtbase-private-devel qt6-qttools-devel
```

Users of other distributions are encouraged to expand upon this guide.

## 2. Optional dependencies

You'll also need to install the following optional dependencies:

Debian/Ubuntu  | Arch/Manjaro | Fedora | Description
---------------|--------------|--------|------------------------------------------------------
`wine64-tools` | ???          | `wine-devel` | Needed to set SDK_WINE=ON config, as described below.
???            | ???          | `onnxruntime-devel` | Needed to build the neuralnet tracker.

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
make -j$(nprocs)
```

The `-j` arg does the compilation in parallel across all your CPUs, so speeds
things up tremendously.

## 6. Install

```sh
make -j$(nprocs) install
```

This installs to wherever the config variable `CMAKE_INSTALL_PREFIX` points to,
by default just `./install`.

## 7. Run

Change to the install's bin directory and try it out:

```
cd install/bin
./opentrack
```

## 8. Variations

You might want to change the directory we install Opentrack to, in which case
modify the `CMAKE_INSTALL_PREFIX` configuration, e.g:

```sh
cmake . -DSDK_WINE:BOOL=ON -DCMAKE_INSTALL_PREFIX:PATH=$HOME/.local
```

To enable the neuralnet tracker also add the ONNXRuntime cmake and include dirs, for example `-DONNXRuntime_DIR=/usr/lib64/cmake/onnxruntime -DONNXRuntime_INCLUDE_DIR=/usr/include/onnxruntime`

and then recompile, etc.

## 9. Package Builds

### Debian/Ubuntu
???

### Arch/Manjaro
???

### Fedora
- Install rpm-build and dnf-plugins-core `sudo dnf -y install rpm-build dnf-plugins-core`
- Download https://github.com/opentrack/opentrack/archive/refs/tags/opentrack-2023.3.0.tar.gz to `~/rpmbuild/SOURCES/opentrack-2023.3.0.tar.gz`
- Create `~/rpmbuild/SPECS/opentrack.spec` with the following contents.
```
Name: opentrack
Version: 2023.3.0
Release: 1%{?dist}
Summary: opentrack is a program for tracking user's head rotation and transmitting it to flight simulation software and military-themed video games.

License: ISC
URL: https://github.com/opentrack/opentrack
Source0: https://github.com/%{name}/%{name}/archive/refs/tags/%{name}-%{version}.tar.gz

BuildRequires: cmake
BuildRequires: git
BuildRequires: onnxruntime-devel
BuildRequires: opencv-devel
BuildRequires: procps-ng-devel
BuildRequires: qt5-linguist
BuildRequires: qt5-qtbase-private-devel
BuildRequires: qt6-qtbase-private-devel
BuildRequires: qt6-qttools-devel
BuildRequires: wine-devel
Requires: onnxruntime

%description
opentrack is a program for tracking user's head rotation and transmitting it to flight simulation software and military-themed video games.

%prep
%setup -q -n %{name}-%{name}-%{version}

%build
%cmake -DSDK_WINE:BOOL=ON -DONNXRuntime_DIR=%{_libdir}/cmake/onnxruntime -DONNXRuntime_INCLUDE_DIR=%{_includedir}/onnxruntime
cd redhat-linux-build
make %{?_smp_mflags}

%install
cat << EOF > opentrack.desktop
[Desktop Entry]
Version=1.0
Type=Application
Name=Opentrack
Comment="opentrack is a program for tracking user's head rotation and transmitting it to flight simulation software and military-themed video games."
Exec=opentrack
Categories=Game
Keywords=gaming
Icon=opentrack
EOF
desktop-file-install --dir=%{buildroot}%{_datadir}/applications opentrack.desktop
install -Dpm 0644 gui/images/opentrack.png %{buildroot}%{_datadir}/icons/hicolor/256x256/apps/%{name}.png
cd redhat-linux-build
%make_install

%files
%{_bindir}/opentrack
%{_datadir}/applications/opentrack.desktop
%{_datadir}/icons/hicolor/256x256/apps/opentrack.png
%{_datadir}/opentrack
%{_libexecdir}/opentrack
%doc %{_datadir}/doc/opentrack
%license

%changelog
* Mon Sep 22 2025 Jason Montleon <jason@montleon.com> [2023.3.0-1]
- Initial Build
```
- Install build dependencies `sudo dnf builddep -y ~/rpmbuild/SPECS/opentrack.spec`
- Build the package `rpmbuild -ba ~/rpmbuild/SPECS/opentrack.spec`
