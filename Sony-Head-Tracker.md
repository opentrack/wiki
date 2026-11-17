# Sony Head Tracker

[Sony Head Tracker](https://github.com/NicholasSlattery/sony-head-tracker) is a free and open-source Windows application that uses the motion sensors inside compatible Sony headphones and earbuds as a three-degrees-of-freedom head tracker for opentrack.

It reads yaw, pitch, and roll from compatible devices and sends the tracking data to opentrack through the **UDP over network** input.

Sony Head Tracker is an unofficial community project and is not affiliated with or endorsed by Sony.

## Requirements

* Windows 11
* A compatible Sony Bluetooth headset or pair of earbuds
* [Sony Head Tracker](https://github.com/NicholasSlattery/sony-head-tracker/releases/latest)
* opentrack

Compatibility depends on whether the device exposes a compatible head-tracker HID sensor.

## Setup

1. Pair the Sony headphones or earbuds using Windows Bluetooth settings.

2. Download and open the latest Sony Head Tracker release.

3. Confirm that the headset appears in Sony Head Tracker.

4. Move the headset and verify that the live yaw, pitch, and roll values change.

5. Open opentrack.

6. Select **UDP over network** as the input.

7. Open the UDP input settings and set the port to:

   ```text
   4242
   ```

8. Select the desired game output, commonly **freetrack 2.0 Enhanced**.

9. Select a filter such as **Accela**, if desired.

10. Press **Start** in opentrack.

11. Face forward and recenter the tracker.

## Repairing the Windows tracker sensor

Windows may pair a compatible headset without correctly exposing or binding its head-tracker sensor.

When this happens:

1. Press **Repair Tracker** in Sony Head Tracker.
2. Approve the Windows administrator prompt.
3. Allow the application to reopen.
4. Confirm that the headset now appears and provides orientation data.

Administrator permission is used for the targeted Windows device-repair operation. Normal orientation data is then sent locally to opentrack over UDP.

Sony Head Tracker does not modify the headset firmware or install a custom kernel driver.

## Limitations

* Tracking is rotational only: yaw, pitch, and roll.
* Positional X, Y, and Z movement is not provided by the headphone sensor.
* Sony Head Tracker must run alongside opentrack.
* Compatibility may vary by headphone model, firmware version, Bluetooth adapter, and Windows Bluetooth stack.
* Some systems may require the Repair Tracker operation after restarting Windows.

## More information

* [Source code and documentation](https://github.com/NicholasSlattery/sony-head-tracker)
* [Latest release](https://github.com/NicholasSlattery/sony-head-tracker/releases/latest)
* [Issue tracker and compatibility reports](https://github.com/NicholasSlattery/sony-head-tracker/issues)
