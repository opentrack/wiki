# Introduction
Easy Tracker was primarely designed to provide best head tracking with Microsoft Kinect V2 IR camera and passive cap markers.

# Easy Tracker vs Point Tracker

## Hardware
While Point Tracker works best with video cameras, Easy Tracker was intended to be used with IR cameras.

## Implementation
Point Tracker is using its own algorithm implementations for point extraction and pose estimation.
Easy Tracker is making use of OpenCV implementations for point extraction and pose estimation.

# Facts
* Only works with Kinect V2 IR camera, for now.
* Do not support "clip" markers. Feel free to request that feature.
* You better use your own custom passive marker rather than the TrackerIR "cap".

# Support
Feel free to open issues if you are having setup problems or if you have feature requests for supporting your hardware.

# References
* [Issue about the birth of Easy Tracker](https://github.com/opentrack/opentrack/issues/915).
* [Initial pull request](https://github.com/opentrack/opentrack/pull/932).
* [Using Microsoft Kinect V2](https://github.com/opentrack/opentrack/wiki/Using-Microsoft-Kinect-V2).
* [How to define vertices](https://github.com/opentrack/opentrack/issues/1141#issuecomment-685762072).