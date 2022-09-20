### PS3 Eye open driver

opentrack now has a standalone driver for the PS3 Eye, and it's mature enough for its existence to be advertised more widely. Now you don't have to pay for (or pirate, for that matter) the CL Eye driver that's buggy, slow, unmaintained and broken with every other Windows 10 update. The crashes are gone and there's less CPU usage. It's also free as in beer.

-    Uninstall any previous driver.
-    Use the zadig program <<https://zadig.akeo.ie>> to install the **libusb-win32** driver onto interface 0 of the camera. Don't use the WinUSB driver!
-    If it fails to work, try connecting the camera onto a USB 2.0 or a USB 3.0 controller that you haven't used yet. Then run zadig again.
-    In Device Manager, make sure the driver is assigned to the device. If it's not, use the "update driver" button to select libusb (it's its own category).
-    If it STILL fails to work, try the procedure again, except this time installing **libusbK** instead of libusb-win32
-    If it doesn't work despite all that, switch to libusb-win32 again (see [[this comment | https://github.com/opentrack/opentrack/issues/1383#issuecomment-1013661144]]).