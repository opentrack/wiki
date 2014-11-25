You can use OpenTrack to make custom VR helmet similar to Oculus Rift with your smartphone.

**Smartphone requirements:**
- 1080p (4,5-6" depending of gogles) screen (720p will have poor quality, but works too)
- gyroscope sensor
- Android operating system
- Samsung galaxy note 4 or LG G3 preffered for Colorcross gogles
- Nexus 5 or Samsung Galaxy S4 prefferred for Cardboard gogles.
- ... more DPI on screen is always better.

**Hardware requirements:**
- smartphone PC USB cable.

**VR gogles you can use:**
- Chinavision ColorCross (best choice, they don't need lens correction, they have large lenses)
- Google Cardboard
- OpenDive / Durovis Dive
- ... and all similar

From left: Open Dive, Colorcross, Google Cardboard
![](https://dl.dropboxusercontent.com/u/73783868/opentrack_vr_tutorial/20141124_235553.jpg)

**1) Connect smartphone and PC to the same network.**
Please use USB connection - it should support 30-60 fps with 1080p video image. Wifi will be too slow.

**a)** Disable Wifi and GSM data on smartphone

**b)** enable USB tethering on smartphone

**c)** make sure PC and smartphone are in the same subnet (you can ping your smartphone from PC).

**2) Install OpenTrack 2.3 on your PC**

**a)** set tracker to FreePie and configure it as seen on image below
![](https://dl.dropboxusercontent.com/u/73783868/opentrack_vr_tutorial/ok_vr.JPG)

**b)** set mappings as you see on images below
![](https://dl.dropboxusercontent.com/u/73783868/opentrack_vr_tutorial/vr_yaw.JPG)
![](https://dl.dropboxusercontent.com/u/73783868/opentrack_vr_tutorial/vr_roll.JPG)
![](https://dl.dropboxusercontent.com/u/73783868/opentrack_vr_tutorial/vr_yaw.JPG)

**c)** set center button in Keys tab.

**d)** enable 5555 UDP port in your PC firewall (for FreePie tracker)

**e)** set protocol to Freetrack 2.0 Enchanced (depend of game)

**f)** on mappings tab set axes invertion (may depend on game) 

![](https://dl.dropboxusercontent.com/u/73783868/opentrack_vr_tutorial/invert_vr.JPG)

**3) Install FreePie Android Client on Your smartphone**

**a)** Freepie Client is located in _your_OpenTrack_installation_directory\clientfiles\android-freepie_

Application name: com.freepie.android.imu-20141024.apk
Remember to enable "allow installation from unknown sources" on your smartphone before install.(You will be prompted with option to go to the settings if you haven't enabled this)

**b)** configure FreePie  Android Client as you see on image below.
Remember - target IP is your PC IP.

![](https://dl.dropboxusercontent.com/u/73783868/freepie/4.png)

**4) Configure Video stream.**

**a)** If you have nVidia and GeForce experience software you can use limelight:
Instruction how to configure:
http://forum.xda-developers.com/showthread.php?t=2505510

**b)** if you have other card, ATI for example you can use Splashtop video stream:
http://www.splashtop.com/downloads

**5) Game configuration**

**a)** Remember, your game need to support non standard Side By Side mode, without 50% horizontal squeeze.
Game need to support resolutions in 8:9 proportions.
For example, 1920x1080 is 16:9 proportion. You need 960x1080 per one eye. Two eyes is 1920x1080 on your screen.

Example of non standard SBS view with correct aspect ratio
![](http://i.imgur.com/dX5u2K6l.jpg)

**b)** if game support only standard SBS view with 50% horizontal squeeze or you using Tridef3D http://www.tridef.com/ you need force game to run in non standard resolution 1920x2160 in 8:9 proportions and it should be resized by streaming software to correct proportions.

Example of standard SBS view with 50% horizontal squezze. Look at egg planets...
![](http://i.imgur.com/pjjjC1il.jpg)
1920x2160 resolution stream should correct it and it should look like non standard SBS in point **a)**.

**6) setting non standard 1920x2160 in 8:9 resolution if game don't support non standard SBS view.**

**a)** if you have Nvidia card you can do this in Nvidia control panel
![](https://dl.dropboxusercontent.com/u/73783868/opentrack_vr_tutorial/nvidia.JPG)

**b)** if you have ATI card you can make it in registry
http://www.wsgf.org/forums/viewtopic.php?t=21972&f=63

**7) Prepare your VR gogles**

Better models of VR gogles have lens adjustment.
Make sure your VR gogles are properly adjusted. 

In my case it was:
I measured a distance between center of eyes and set centers of lenses to this value.
My distance between centers of eyes is 40mm.

This is personal settings, adjustment method depend of your eyes, **you need to prepare VR for your own way**.
**If you have problem with adjusting gogles consult it with your eye-doctor.**

**8) Run everything**

**a)** Start Opentrack

**b)** start Freepie Tracker on your smartphone

**c)** start streaming game in correct resolution

**d)** put helmet on head

phone should be mounted in headset at the same position as on image below (don't laugh):

![](http://i.imgur.com/MLRiiEPl.jpg)

**e)** use your defined before center button

**9) Enjoy your cheap homemade VR!**

**Here is Video: http://youtu.be/3bH46VKHLUM**