The following are the common issues accounting for more than 75%
reported issues.

Most of the issues no longer need addressing in the 2.3 branch. Let's keep them however as long as 2.3 isn't considered stable and 2.2 obsolete.

### PointTracker tracker doesn't work!

Go to 'model' tab in the tracker settings, and input the clip's
dimensions.

If you have a very flashy result, go to 'camera' tab in the tracker settings and try to play with threshold asettings. If you still have difficulties to get your points detected, change gain/exposure setting in the driver of your camera. In general the "auto threshold" option is a benefit.

### Tracking's too slow or jumpy!

Set up the Accela filter. [It has its own wiki page.](https://github.com/opentrack/opentrack/wiki/Accela-in-opentrack-2.3)

### I don't want to make a LED clip!

Then track a piece of paper as per [[aruco tracker]] wiki page.

### Keybindings ignored in games!

Game running as administrator with opentrack as regular user. Run both
as administrator or both as user. You do **not** need to run opentrack as admin by default.

### freetrack protocol doesn't work!

Try moving the software directly to a drive, e.g. "c:/opentrack".
Windows Vista and possibly others have issues with permissions. Can also
use one of the "c:/program files/" directories instead of the drive's
root.

This happens most often with Elite Dangerous and isn't opentrack's fault.

### opentrack crashes

Make sure you don't have "Gigabyte OC Guru" installed. The software does unseemly things to other running processes and is responsible for the crashes. The same problem's caused by the Moonlight streaming software.

### I want to donate to the project!

The opentrack project doesn't receive any donations. Please donate to the [Electronic Frontier Foundation](https://www.eff.org/) instead.