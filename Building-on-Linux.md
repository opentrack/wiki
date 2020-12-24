Opentrack does not provide binaries for Linux users. The following is a brief, missing guide on compiling opentrack for Linux.

## Building on Debian, Ubuntu, etc.

The following dependencies are for **Debian-based** systems, however it should give users of other distros a rough idea of what they will need to hunt for in their own package manager. Users of other distributions are encouraged to expand upon this guide.

### Dependencies
* `cmake`
* `git`
* `qttools5-dev`
* `qtbase5-private-dev`
* `libprocps-dev`
* `libopencv-dev`

**Note:** While opentrack will build without OpenCV, it will only compile with a very minimal subset of its functionality, making it of little use to the average user who does not have very specific usage requirements. 

### Compiling

Compiling the project is the same as with any cmake project:

```bash
git clone https://github.com/opentrack/opentrack
cd opentrack/
cmake .
make
make install
```

**Note:** The resulting build output will be placed in the `install/` directory. It will not 'install' itself anywhere outside of the current directory.
