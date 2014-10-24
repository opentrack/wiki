The page describes concepts used throughout the software.

**Tracker** is software submitting head rotation and translation data to
the main module of the program.

**Sensor** is the physical device from which the running tracker
receives data and processes it. Typically it's a webcam or some kind of
inertial measurement device.

***

**Filter** ensures that data received from the tracker is
[idempotent](http://en.wiktionary.org/wiki/idempotent) enough when the
user doesn't command any particular change in input. It's necessary for
webcam-based trackers, as these process image frames and compute the
pose using numerical methods. In that case, software operation without a
filter is commonly referred throughout the userbase as "jumping all
over".

Please note that in the case of inertial numerical-integration trackers
(Rift, Hydra, gyro/mag/acc), filters aren't that much, or at all
necessary. This is because the range of input is much larger. If it's
360 deg, with webcam trackers limited to 80, there's less noise by
virtue of higher input range. Typical sensor amount, hardware quality,
software implementation correctness, magnetometer calibration and
interference, caveats apply.

***

**Protocol** transmits data from the software to whichever
game/simulation software the user decides to use. Since the target
software doesn't have any idea of opentrack running, some glue code must
be used. As such, selecting a protocol is required for the tracking
process.

***

**Mapping** defines what kind of output is transmitted to target
software. X degrees yaw is transformed into Y degrees yaw to be received
by the game by the mapping, as defined by the user. Here, Catmull-Rom
splines are used instead of any formal function, for the sake of ease of
use.

**Origin**/center position is the orientation and position pair the
software defines as looking perfectly forward, with no displacement.
This particular position isn't saved between software runs. Instead, a
keybinding's used to allow the user to shift in his chair without
switching whatever he's doing into the software's interface.
