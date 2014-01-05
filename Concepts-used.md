The page describes concepts used throughout the software.

**Tracker** is software submitting head rotation and translation data to the main module of the program.

**Sensor** is the physical device from which the running tracker receives data and processes it. Typically it's a webcam or some kind of inertial measurement device.

**Filter** ensures that data received from the tracker is [idempotent](http://en.wiktionary.org/wiki/idempotent) enough when the user doesn't command any particular change in input. It's necessary for webcam-based trackers, as these process image frames and compute the pose using numerical methods. In that case, software operation without a filter is commonly referred throughout the userbase as "jumping all over".