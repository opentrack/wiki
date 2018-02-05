Accela in opentrack 2.3 no longer contains many overly complicated settings.

**Sensitivity** makes small movements take effect slower. This is useful to prevent natural head shaking resulting in the view swimming all over the virtual cockpit. As well as natural tracker inaccuracy causing jumping around each frame, since very slightly different pose is returned each time.

There are two **sensitivity** sliders, for rotation and translation each. They're expressed in different units.

**Smoothing** makes movement more regular but delayed. This is for a pleasant, smooth experience. It doesn't help at all with noise removal.

**Deadzone** ignores minor movement completely. It can be useful for extremely noisy input. Try not to use it excessively to avoid losing precision. For camera-based trackers, rotation deadzone of 0.06 degrees is already pretty high.