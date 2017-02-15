### How to get best calibration results

This is my method of calibrating and it works every time.

At start, move your head up as if pitching up

- *start*
- Make left-right yaw motion
- Move head slightly lower
- If moved to the limit of where you want to pitch down, click "toggle calibration" to *stop*, we're done
- Otherwise, repeat from *start*

### Calibration interface

To start and stop calibration procedure, you must press the same "Toggle calibration" button. The button looks pressed when calibrating, pressing it again stops calibration and saves the values.

As per above, there's no separate button for ending calibration. There's some user confusion hence I'm spelling it out explicitly.

cheers, sthalik

Here is a link to a short video showing the calibration process:
https://youtu.be/ZDz-bholoMo

## Try not to overcalibrate
Do not try to make the same movements for too long, otherwise the algorithm won't work, just make the movements and then re-click the button.

## Why is it like that?

A purely statistical algorithm tries to guess the axis of rotation. It's better to supply many different poses so the code has more data to work with. No need to overdo it - the process in the first paragraph is enough.

http://coub.com/view/chtk7