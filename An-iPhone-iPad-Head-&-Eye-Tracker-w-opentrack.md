Experience the Eyeware Beam app's responsive 6DOF head tracking with more than 200 of your favorite driving and flight simulator, and first-person shooter PC games compatible with opentrack.

## [App Store Download: Eyeware Beam](https://apps.apple.com/us/app/eyeware-beam/id1538790472)

Livestream your online arena and MOBA gaming content with our accurate eye tracking overlay on Twitch, Youtube, or Facebook to share wherever you are looking at with your audience in real-time.

The free in beta Eyeware Beam app turns your iPhone or iPad, that supports Face ID with its built-in TrueDepth camera, into a reliable and precise, multi-purpose head and eye-tracking tool. Our app works as the input source, enabling a full range of in-game head motion. Use Eyeware Beam to add depth to your gaming and streaming experience with responsive, intuitive head movement controls.

There is no expensive headset, glasses, or additional hardware needed.

The TrueDepth technology produces a depth map of your face by projecting 30,000 infrared points that are recorded and processed by the smartphone chip’s neural engine. Eyeware Beam takes advantage of this technology to provide you with an app that generates an accurate head pose and eye tracking signal comparable to expensive proprietary devices from Tobii or TrackIR. 

![Eyeware Beam](https://scontent.ffxe1-1.fna.fbcdn.net/v/t1.6435-9/202797321_311437187386312_1306328837750275810_n.png?_nc_cat=105&ccb=1-5&_nc_sid=e3f864&_nc_eui2=AeGxMkdyjfifEjRTCxscQ5_CFtL14DCVcj8W0vXgMJVyP4gBPxOijawUEwBa0jGUXH-RN5SYELZ-JAqDYLXE68u4&_nc_ohc=vgrvdBrk5zIAX_gEG5A&_nc_ht=scontent.ffxe1-1.fna&oh=c1c98774e29080a366a08d563d1852d6&oe=616CDD6A)
### [Quickstart guide](https://beam.eyeware.tech/tech-support/quickstart-guide-eye-head-tracker/) sourced from Eyeware Beam:

## **Pre-setup Requirements Checklist**
* Windows 10 only on PC or laptop (Mac support not yet available)
* 2GB of free space on your computer
* iPhone or iPad has “Face ID 1” with iOS 13+
* Eyeware Beam app on your iPhone/iPad is open at all times
* One phone support (or something to keep the phone stable on)
* Compatible PC game 

## Instructions

### Setup:

Step 1: Set your iPhone/iPad and computer to both use the same Wi-Fi network. This step is necessary because your IP address on your phone and computer must match.

Step 2: Set all other Wi-Fi networks on your iPhone/iPad from “Auto-Join” to “off”).
**Open your iPhone/iPad settings. Tap Wi-Fi. Tap the Wi-Fi network for which you want to turn off Auto-Join. *Toggle Auto-Join off. This is only needed if you have more than one Wi-Fi connection available (i.e. cell phone network + home wiki network).

Step 3: Select the computer screen you will use in Windows Display Start > Settings > System > Display. This is only necessary if you use multiple computer monitors.

Step 4: On the right side of your computer screen taskbar, select the Wi-Fi network icon. Under the name of the Wi-Fi network that you’re connected to, select Properties. Under Network profile, select Private.

Step 5: Download our computer app counterpart 2 to connect your iPhone/iPad to your PC or laptop screen where you will use the head and eye-tracker.
**note: Eyeware Beam will not work without this computer app from step 1, the iPhone/iPad app from the app store, opentrack 2 to enable head tracking, and OBS Studio to enable streaming with eye-tracking.

Step 6: Add the Eyeware Beam computer application (Beam.exe) as an exclusion to your Windows 10 firewall.
Press Windows key on keyboard → type “Firewall” → “Firewall & Network Protection” → “Advanced Settings” → Inbound Rules → Actions → New Rule → Program → This Program Path → Browse → Beam.exe->Finish*

Step 7: After Installing the computer app, enter your IP address that is shown on the Beam iPhone app screen when prompted. 1:57 – 2:40

Step 8: Place your iPhone/iPad next to your PC/laptop screen as directed. 2:40 – 3:16

Step 9 Click on each white hexagon dot to calibrate head and eye-tracking. 3:16 – 4:25

Step 10: (optional) Find the application now running at the bottom right of your computer. Click on each white hexagon dot to calibrate the gaze bubble. 3:16 – 4:25

*Note: If you can’t find the Eyeware Beam computer application on your screen, it is still running in the background processes. You can find the app with the purple logo in the system tray, usually located at the bottom right of your screen.

Step 11: Modify Eyeware Beam computer application “settings.”

11a: Turn on opentrack Stream by moving the toggle button to the right

11b: The number 4242 should already be input to the opentrack Input Port. If it is not, please add it.

Step 12: You must download any of following applications on your computer to run head tracking in games or stream your eye gaze. Our Eyeware Beam app only transmits your movements from your iPhone/iPad to your computer. opentrack and/or OBS Studio is what relays these movements into your game or stream.

13a: Download OpenTrac  (free) to enable head-tracking and enter these settings
or

13b: Download OBS Studio (free) to enable streaming for eye-tracking and enter these settings
To Play Games
With opentrack

Step 14: Open the opentrack software on your computer and choose the following:

14a: Select Input = UDP over network, port 4242.

14b: Open your compatible PC gam  in Options > Game Detection, press + button and add the executable of an installed game that supports the Freetrack protocol > Select OK

14c: Press Start in opentrack .
*Note: If tracking is inverted, in opentrack go to Options > Output and check to Invert either the *Yaw, Pitch or Roll.

Optional: You can download this settings profile and add it as yours for a good selection of head tracking optimized settings. In order to add it to your opentrack, you need to:

Launch opentrack.

Click on Profile > Open configuration directory.

Place the profile in said directory.

Step 15: Open your compatible PC gam  from your computer as your normally do and head tracking will be working. Make sure the Eyeware Beam app on your iPhone/iPad continues to remain open at all times.
Congrats, your game should now be working with head tracking. Enjoy!

Visit [Eyeware Beam's support website for any questions](https://beam.eyeware.tech/tech-support/)
