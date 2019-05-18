# Introduction
[Microsoft Kinect V2](https://developer.microsoft.com/en-us/windows/kinect) can be used in multiple ways as an Open Track Input device. Regardless which Kinect Input solution you will use, you must first and foremost make sure your Kinect is installed properly.

# Installation
We recommend you mount your Kinect above your screen where it should be at head level. At any time during use, your head should remain at least 50 cm away from the Kinect sensor. To make sure this is the case your rest position should be around 70cm away from Kinect.
For mounting, you can use a tripod with flexible feet to place it directly on top of your monitor, or have it grab on your monitor arm. Here are a few pictures illustrating those solutions:

<a href="https://user-images.githubusercontent.com/6508892/57972625-8b92f080-799d-11e9-85a4-978e77468566.jpg"><img alt="Tripod" src="https://user-images.githubusercontent.com/6508892/57972625-8b92f080-799d-11e9-85a4-978e77468566.jpg" width="25%" height="25%"></a>
<a href="https://user-images.githubusercontent.com/6508892/57972597-0a3b5e00-799d-11e9-89a3-2aabcc90738a.jpg">
<img alt="Kinect Monitor Mount" src="https://user-images.githubusercontent.com/6508892/57972597-0a3b5e00-799d-11e9-89a3-2aabcc90738a.jpg" width="25%" height="25%"></a>
<a href="https://user-images.githubusercontent.com/6508892/57973876-e3d2ee00-79af-11e9-9866-be1cb6207a7b.jpg">
<img alt="Kinect Elite" src="https://user-images.githubusercontent.com/6508892/57973876-e3d2ee00-79af-11e9-9866-be1cb6207a7b.jpg" width="25%" height="25%"></a>

<a href="https://user-images.githubusercontent.com/6508892/57972787-88006900-799f-11e9-978d-ffa80f51fa6c.jpg"><img alt="Tripod with extension" src="https://user-images.githubusercontent.com/6508892/57972787-88006900-799f-11e9-978d-ffa80f51fa6c.jpg" width="25%" height="25%"></a>
<a href="https://user-images.githubusercontent.com/6508892/57972774-58e9f780-799f-11e9-8584-7ea7880d3a27.jpg">
<img alt="Kinect Arm Mount" src="https://user-images.githubusercontent.com/6508892/57972774-58e9f780-799f-11e9-8584-7ea7880d3a27.jpg" width="25%" height="25%"></a>
<a href="https://user-images.githubusercontent.com/6508892/57972917-f0037f00-79a0-11e9-8196-69cbaa23b7f4.jpg">
<img alt="Kinect Arm Mount detail" src="https://user-images.githubusercontent.com/6508892/57972917-f0037f00-79a0-11e9-8196-69cbaa23b7f4.jpg" width="25%" height="25%"></a>

Once you are happy with your installation you should configure Open Track to use your Kinect.

# Trackers

Open Track offers two Kinect input solutions, also called tracker.

## Kinect Face Tracker

Since it does not require any extra accessories, this is the easiest and fastest way to get your Kinect face tracking up and running. Just select Kinect Face as your Open Track Input and you are ready to go. 

Once you start Open Track, the camera image should be displayed in the preview area. As soon as Kinect picks up your face the preview shows a bounding rectangle around it. To speed up face tracking initialisation you should slowly move your face around away from the Kinect. Raising your hands up also helps the initialisation process.

<a href="https://user-images.githubusercontent.com/6508892/57974353-1af8cd80-79b7-11e9-8127-3b48553ef690.png">
<img alt="Kinect Face Tracker" src="https://user-images.githubusercontent.com/6508892/57974353-1af8cd80-79b7-11e9-8127-3b48553ef690.png" width="75%" height="75%"></a>

While straight forward to setup Kinect Face Tracker may fall short of your expectations in terms of range and precision. Luckily for you, you can use the following Tracker instead. 

## Easy Tracker

This Tracker is very similar to Open Track Point Tracker or [TrackerIR by NaturalPoint](https://www.naturalpoint.com/trackir/).

To use it you will need to wear a hat. We actually do not recommend using TrackIR hat clip, shown here on the left, as it results in a noisier signal. The recommended solution is to build your own custom hat using your favourite cap and Motion Capture Markers.

<a href="https://user-images.githubusercontent.com/6508892/57974369-454a8b00-79b7-11e9-8fb2-bef5ea441e67.jpg">
<img alt="Hats" src="https://user-images.githubusercontent.com/6508892/57974369-454a8b00-79b7-11e9-8fb2-bef5ea441e67.jpg" width="25%" height="25%"></a>
<a href="https://user-images.githubusercontent.com/6508892/57974380-585d5b00-79b7-11e9-8883-6723663a2d27.jpg">
<img alt="Custom Hats" src="https://user-images.githubusercontent.com/6508892/57974380-585d5b00-79b7-11e9-8883-6723663a2d27.jpg" width="25%" height="25%"></a>

Make sure you configure Easy Tracker to use your Kinect IR Sensor and provide the specs of your custom hat.
For more information about Easy Tracker configuration see our [Easy Tracker documentation](https://github.com/opentrack/opentrack/wiki/Easy-Tracker).

<a href="https://user-images.githubusercontent.com/6508892/57974362-306df780-79b7-11e9-8282-652ba1d80ea1.png">
<img alt="Easy Tracker" src="https://user-images.githubusercontent.com/6508892/57974362-306df780-79b7-11e9-8282-652ba1d80ea1.png" width="75%" height="75%"></a>