### opentrack settings
1. don't rely on "smoothing" at all. It's being removed. Only sensitivity (renamed to smoothing) and deadzone exist. It's completely gone in the next stable release (2.4.0).
2. lower the camera FOV to 56 deg; note one of two camera types are unable to work other than 75 deg.
3. use brighter LEDs.
4. use auto-threshold **always**. set it to slightly bigger (15 to 20%) pixel size than your LEDs.
5. for red LEDs, select "red only" in PT settings. if you have blue LEDs, report it as a bug and they'll be implemented.

### ps3 eye camera settings

1. play with camera gain until getting white LEDs with not much noise, and without excessive light bloom. **always** use full exposure, only change gain.
2. use a floppy filter as a circle stuffed from outside toward the camera lenses. may also use non-exposed analog camera film. bright background details may confuse the tracker about the point centers.
3. set color correction to all the same values, don't mess around with them at all.
4. **never**use 320x240. don't use 75 Hz for 640x480 as it corrupts the image. only 60 Hz and below gives a clean image.

### accela filter

1. never use "smoothing". it's gone in 2.4.0 and it doesn't work like you think.
2. don't exceed a deadzone of 0.06.
3. set rotation sensitivity to between 0.35 and 0.45
4. longer input range for yaw and pitch will make the movement move smooth overall, but it depends on sitting distance, screen size, and general comfort.