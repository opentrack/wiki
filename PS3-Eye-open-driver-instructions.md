### PS3 Eye open driver

opentrack now has a standalone driver for the PS3 Eye, and you don't have to pay for (or pirate, for that matter) the CL Eye driver that's buggy, slow, unmaintained and broken with every other Windows 10 update.

### Instructions

1. Open the Windows Device Manager.
2. Uninstall any existing closed-source driver.
    * ![image](https://user-images.githubusercontent.com/1896811/201041773-2dbfb0e4-75f9-41b2-82d2-1052f8366669.png)
3. Install the [libusb inf wizard](https://github.com/opentrack/opentrack/files/8797230/libusbK-inf-wizard.zip).
    * ![image](https://user-images.githubusercontent.com/1896811/201042346-be2f3182-392a-4333-819a-7e0ba7be46f7.png)
    * ![image](https://user-images.githubusercontent.com/1896811/201042399-a4fcbd10-d019-4f02-87f1-adcf1d3f9fb4.png)
    * ![image](https://user-images.githubusercontent.com/1896811/201042448-046119d9-7662-4cc3-a4be-e5f324b2ff9a.png)
4. The open driver should now become available in opentrack.
    * ![image](https://user-images.githubusercontent.com/1896811/201042508-b0695163-ef45-4caa-8c61-db9681e6ed25.png)

### Credits

The instructions were originally written by weczi of [IRTrack](https://www.irtrack.pl/) <sup>[\[1\]](https://www.irtrack.pl/download/ps3-open-driver/)</sup>. Used with permission.
