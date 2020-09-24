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

# Model coordinate system
Each marker is matched to a vertex in the model the camera is tracking. To be able to compute the model pose and thus the pose of the head it is attached to, Easy Tracker needs to understand the model geometry.

Therefore you need to tell Easy Tracker the arrangement of your markers. This is done by giving your markers coordinates in the proper coordinates system of arbitrary origin. I recommend you use the top marker as your origin and thus set it's coordinates to (x:0,y:0,z:0), then work out the coordinates of the other markers. Units are in millimetres.

While in theory you can pick any origin for your model's coordinate system its axis are defined by Kinect itself. If you are sitting in front of your Kinect you can think of it like this:
* X axis is horizontal and parallel to your Kinect, left is negative and right is positive.
* Y axis is vertical and parallel to your Kinect, up is negative and down is positive.
* Z axis is horizontal and perpendicular to your Kinect, forward is negative and backward is positive.

# Support
Feel free to open issues if you are having setup problems or if you have feature requests for supporting your hardware.

# References
* [Issue about the birth of Easy Tracker](https://github.com/opentrack/opentrack/issues/915).
* [Initial pull request](https://github.com/opentrack/opentrack/pull/932).
* [Using Microsoft Kinect V2](https://github.com/opentrack/opentrack/wiki/Using-Microsoft-Kinect-V2).
* [How to define vertices](https://github.com/opentrack/opentrack/issues/1141#issuecomment-685762072).