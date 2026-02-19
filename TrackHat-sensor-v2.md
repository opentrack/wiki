# Using the Trackhat Sensor V2 head tracker with opentrack

The **Trackhat Sensor V2** is a plug-and-play head tracking sensor that offers low-latency 6DOF tracking using a specialized high framerate IR sensor. It works with both the official **opentrack** releases and the customized **Trackhat opentrack** version. 

## 🔧 Requirements

- [Trackhat Sensor V2 head tracker](https://www.trackhat.org/sensorv2) 
- Windows 7 or later
- [Trackhat opentrack](https://www.trackhat.org/trackhat-opentrack) (Trackhat’s customized fork)
- [opentrack (official releases)](https://github.com/opentrack/opentrack/releases)

---

## Option 1 (recomended): Using TrackHat opentrack.

Trackhat provides a customized build of opentrack, which includes:

- Built-in support for Sensor V2
- Massively simplified UI, with all additional options and features not required for head tracking with the Sensor V2 removed.
- Automatic update prompting from TrackHat's server
- Optimized filters and mappings
- The below instructions are an abridged version of the [full installation guide](https://www.trackhat.org/manual) 

1. **Download Trackhat opentrack**
   - Visit [trackhat.org/pages/downloads](https://www.trackhat.org/trackhat-opentrack).
   - Download the latest **Trackhat opentrack** ZIP package.

2. **install and start the Application**
   - Run the Trackhat opentrack installer
   - Start the program

3. **Start Tracking**
   - The Trackhat opentrack version will auto-detect your Sensor V2 head tracker.
   - Click **Start** to begin tracking.
   - Settings are pre-configured for best results with Sensor V2, but can be customized in the mapping tool to suit your needs.

## Option 2 (Advanced): Using regular opentrack.

Occasionally, for diagnostic purposes or specific customisations, some users may need to use the regular version of opentrack with their sensor V2.

1. **Install opentrack**
   - Download and install the latest version from the [opentrack GitHub Releases](https://github.com/opentrack/opentrack/releases).

2. **Configure opentrack**
   - Launch opentrack.
   - In the **Input** dropdown menu, choose 'neuralnet tracker'
   - Open the settings for the neauralnet tracker by cicking the icon next to it (🔨)
   - On the 'camera name' dropdown, select 'Trackhat sensor'. Leave all other options as defaults
   - Select 'Freetrack 2.0 enhanced' as the output

3. **refining head tracking**
   - Remember that **the default version of opentrack is not readily optimized for the sensor V2** and will require lots of tuning
   - Click **Start**.
   - Movement should be visible in the preview window.
   - Adjust mappings and filters as desired.

---

## Notes 📝

- The Sensor V2 works as a standalone 6DOF tracker — no additional IR tracking needed.
- It can also be used in hybrid mode with IR headgear.

---

## FAQ ❓

**Q: Can I use the Sensor V2 with Linux or macOS?**  
A: Official support is currently Windows-only. Linux/Mac support is community-driven and not guaranteed. 

**Q: What’s the difference between opentrack and Trackhat opentrack?**  
A: Trackhat opentrack includes enhancements and preconfigured settings tailored specifically for Trackhat hardware, as well as a streamlined UI and automatic updates.

**Q: Are there advantages to using the TrackHat sensor V2 instead of a mobile phone camera?**
A: The Sensor V2 has a higher framerate, infrared sensor, and infrared illumination all of which allow head tracking in all lighting conditions, as well as a larger tracking area, faster speed, and much greater ease of use.

---

Need help? Visit [Trackhat.org](https://trackhat.org) and use the chat icon in the bottom right hand corner to get support (note that this functions as an email support system, not a live chat)

---

TrackHat has worked with opentrack for almost a decade to ensure high compatibility with the project, and we are exceedingly grateful to Stanislaw for his tireless dedication to it.
