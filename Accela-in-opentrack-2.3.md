Accela in opentrack 2.3 no longer contains many interacting and hard to understand settings.

**Sensitivity** makes small movements take effect slower. This is useful to prevent natural head shaking resulting in the view swimming all over the virtual cockpit. As well as natural tracker inaccuracy causing jumping around each frame, since very slightly different pose is returned each time.

There are two **sensitivity** sliders, for rotation and translation each. They're expressed in different units.

**Rotation nonlinearity** affects how sensitivity works. Putting the slider to the right makes tiny movements more and more delayed. Putting it to the right too much makes the filter suddenly jump when the movement's no longer tiny.

A setting of 1.05 up to 1.15 is usually right for a camera-based tracker. The right value depends on the exact device.

**Smoothing** makes movement more regular but delayed. This is for a pleasant, smooth experience. Don't mistake it for noise removal.

**Deadzone** ignores minor movement completely. It can be useful for extremely noisy input. Try not to use it excessively to avoid losing precision. For camera-based trackers, rotation deadzone of 0.05 degrees is already pretty high.