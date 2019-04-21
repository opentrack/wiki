# Introduction
Easy Tracker was initially developed to work together with Kinect V2 IR camera and passive cap markers.
In fact after spending a fair amount of time trying to get Point Tracker to work reliably with Kinect we eventually gave up and came up with Easy Tracker.

# Easy Tracker vs Point Tracker

## Hardware
While Point Tracker was primarily designed to work with video cameras, Easy Tracker was intended to be used with IR cameras.

## Implementation
Point Tracker is using its own algorithm implementations for point extraction and pose estimation.
Easy Tracker is making use of OpenCV implementations for point extraction and pose estimation.

# Facts
* Only working with IR cameras.
* Only tested with Kinect V2 IR camera.
* Only support cap markers.
* Noisy signal, you will need to max out Accela filter settings.

# Support
If you are having problems getting Easy Tracker to work please open an issue.
Feel free to open issues if you have feature requests for supporting your hardware.

# References
* [Issue about the birth of Easy Tracker](https://github.com/opentrack/opentrack/issues/915).
* [Initial pull request](https://github.com/opentrack/opentrack/pull/932).