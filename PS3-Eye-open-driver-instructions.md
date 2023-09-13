### PS3 Eye open driver

opentrack now has a standalone driver for the PS3 Eye, and you don't have to pay for (or pirate, for that matter) the CL Eye driver that's buggy, slow, unmaintained and broken with every other Windows 10 update.

### Instructions

1. Open the Windows Device Manager.

    * ![image](https://user-images.githubusercontent.com/1896811/201043795-d0aa9ad4-700b-48a4-be1d-dcf0a5cbd6cd.png)

2. Uninstall any existing closed-source driver.

    * ![image](https://user-images.githubusercontent.com/1896811/201041773-2dbfb0e4-75f9-41b2-82d2-1052f8366669.png)

3. Install the [libusbK development kit](https://github.com/opentrack/opentrack/files/12601627/libusbK-3.1.0.0-setup.zip)<sup>\[[original](https://sourceforge.net/projects/libusbk/files/libusbK-release/3.1.0.0/)\]</sup>.

    * ![image](https://github.com/opentrack/opentrack/assets/1896811/f6b46deb-0875-4f0f-bd3e-58189155e499)

4. Install the [libusb inf wizard](https://github.com/opentrack/opentrack/files/8797230/libusbK-inf-wizard.zip)<sup>\[[original](https://sourceforge.net/projects/libusbk/files/libusbK-release/3.1.0.0/)\]</sup>.

    * ![image](https://user-images.githubusercontent.com/1896811/201042346-be2f3182-392a-4333-819a-7e0ba7be46f7.png)
    * ![image](https://user-images.githubusercontent.com/1896811/201042399-a4fcbd10-d019-4f02-87f1-adcf1d3f9fb4.png)
    * ![image](https://github.com/opentrack/opentrack/assets/1896811/40a0504e-e092-4043-992f-9771875ecc97)

4. The open driver should now become available in opentrack.

    * ![image](https://user-images.githubusercontent.com/1896811/201042508-b0695163-ef45-4caa-8c61-db9681e6ed25.png)

### Credits

The instructions were originally written<sup>\[[original](https://www.irtrack.pl/download/ps3-open-driver/)\]</sup> by weczi of [IRTrack](https://www.irtrack.pl/). Used with permission.
