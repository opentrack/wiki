Camera offset is for camera-based trackers only, when camera's not pointing directly on the model.

**Don't use the following procedure after opentrack 2.3.0 rc13. Use automatic camera offset instead.**

- disable "center on startup" in options
- start tracking
- adjust camera offset until game data yaw/pitch/roll says zero, zero, zero
- you can reenable "center on startup" now

Camera offset improves centering and zooming. For zooming, no longer is pitch and moving upward applied.