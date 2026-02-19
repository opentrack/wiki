Since Steam Client's Update 2022-09-21, Steam detects Wiimotes and takes full control over it, which makes opentrack not detect it as a real Wiimote anymore. But there's a workaround: Adding the Wiimote to Steam Client's blacklist:

1. Connect Wii Remote to PC, find the VID/PID of your controller (on Windows, open control panel > devices and printers > go to the properties of the wii remote > hardware > select Bluetooth HID device > details > Hardware IDs and copy the VID/PID)
These are 16 bit numbers, so only last 4 hex digits, you may omit leading zeros:
VID&0002057e_PID&0330=> "57e/0330"

2. Close Steam (e.g. Steam > Exit).

3. Navigate to and open with Notepad: [STEAM INSTALLATION] / config / config.vdf

4. Do a search for: controller_blacklist

   - If it doesn't exist, go to the end of the file and before the last }, insert a new line then paste in:
    "controller_blacklist" "57e/0330"
   - If it does exist add the VID/PID to it:
    "controller_blacklist" "57e/0330"
    (if it already contains a VID/PID, insert a comma and then the DS5 VID/PID e.g. "45e/2e0,54c/ce6")

5. Save and close

