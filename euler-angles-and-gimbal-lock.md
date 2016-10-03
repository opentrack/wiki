### Gimbal lock problem

This article isn't about opentrack per se.

### The what

When we talk about gimbal lock, we talk about the unfortunate existence of multiple solutions. We want the "**canonical**"  [2] solution but it returns 180 roll and some others rather than some pitch and some yaw with little roll. What now?

### The how

- Divide the rotation amount [3] in the proper representation by four [1]
- Convert to Euler (actually Tait-Bryan since it's yaw, pitch, and roll).
- Multiply that Euler triplet by four

### The why

* [1] Floating-point numerals' exponent is base 2. Dividing by four, eight, sixteen doesn't give us inaccuracy as compared to dividing by three, five, etc.
* [2] The one we care about, the one everyone cares about.
* [3] Convert to axis-angle. Divide the angle by four. Leave axis alone. Convert back.

### The aftermath

Profit.

cheers,
sthalik