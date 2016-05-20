This guide is intended for use to get up and running fairly quickly. It is not designed for explaining the intricacies of all the options/settings that are available.

## Quick Start Video: 
[![opentrack Quick Start Video](http://img.youtube.com/vi/QYmHab6CGgo/0.jpg)](https://www.youtube.com/watch?v=QYmHab6CGgo "opentrack Quick Start Video")

##Video of the calibration process: 
[![opentrack Calibration Video](http://img.youtube.com/vi/ZDz-bholoMo/0.jpg)](https://www.youtube.com/watch?v=ZDz-bholoMo "opentrack Calibration Video")

Below is the opening screen for OpenTrack. The version number is displayed in the top. The area marked "no video" displays the camera output once the program is running. The octopus will rotate as you move your head. Below them are the raw tracker and game data displays. 
![Main Window](https://www.dropbox.com/s/6oe8p7zcvytu25j/mainscreen.png?dl=1)

1 - clicking here will take you to the Tracker selection.

2 - clicking here will take you to the Protocol selection.

3 - clicking here will take you to the Filter selection.

4 - clicking here will take you to the Options window.

5 - clicking here will take you to the Mapping window.

Here are the options for the tracker selection:
![Tracker Selection](https://www.dropbox.com/s/c5saj261sg3j3wy/tracker%20selection.png?dl=1)
In the Tracker selection you define the type of tracking method to be received by opentrack. For example if you have a tracking clip with IR-leds you need 'Pointtracker 1.1', but if you want to use your phone as a tracking device you need to select the 'FreePIE UDP receiver'.

Here are the options for the protocol selection:
![Protocol Selection](https://www.dropbox.com/s/03z9cla0jj59y62/protocol%20selection.png?dl=1)
The protocol section is for defining how to communicate the movement data from opentrack to the game. Many games will work using the 'freetrack 2.0 Enhanced' protocol, but some games do have their own protocol, for example the Flight Simulator games. In games that don't support any form of headtracking natively you can also map the headtracking to the mouse coordinates, so that you can move the mouse with your head.

Here are the options for the filter selection:
![Filter Selection](https://www.dropbox.com/s/ezgmk3krds6cfkr/filter%20selection.png?dl=1)
Here are the options for the options window:
![Options](https://www.dropbox.com/s/9ur7l0udhyuaf71/option%20screen.png?dl=1)

Here is the Mapping window where you can set curves for the six DOF. The numbers on the left represent the degrees of movement in the game, and the numbers along the bottom represent real world movement. In this window you can see that I have a dead space of approx 8 deg and at 15 degrees movement in game will be 180 deg for the yaw setting. In other words as I turn my head left and right and my view reaches the edges of my monitor I get max movement in game. If you tick the Asymmetric box you can set curves independently for right/left movement.

![Mapping](https://www.dropbox.com/s/dhwdy1ggyqhs3n6/mapping%20screen.png?dl=1)

I use a 3 point IR led clip and a PS3 eye camera, a very good set-up to use with Opentrack. To get up and running quickly choose the Tracker, Protocol, and Filter you want to use. Clicking on the three dots next to the drop down takes you to additional settings for the chosen item. The option window has four tabs, Shorcuts, Camera, Output, and Game Detection.

If you are using Point Tracker you will need to click the 3 dot tab and enter your camera data in the pop-up that appears.

Once you are ready click Start and off you go. On the main wiki page are some links that lead to pages with additional information on various parts of OpenTrack.