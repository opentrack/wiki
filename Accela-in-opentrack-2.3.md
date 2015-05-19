Accela in opentrack 2.3 no longer contains many interacting and hard to understand settings.

**Smoothing** reduces value changes between frames that happen with noisy trackers like ones based on webcams.

**Sensitivity** causes small movements to lag behind. This is useful to prevent natural head shaking resulting in the view swimming all over the virtual cockpit.

Separate **sensitivity** values exist for rotation and translation. These are expressed in different units with arbitrary scales.

**Deadzone** ignores minor movement completely. It can be useful for extremely noisy input. Try not to use it excessively to avoid losing precision.