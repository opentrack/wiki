The following are the common issues accounting for more than 75%
reported issues.

# Tracking won't work!

Go to the 'mapping' window, look at rectangles with blue background, and
ensure they have any content.

You can add a control point with left mouse button. Right button removes
a control point. Existing points move by dragging with left button.

Changed in development branch prior to 20141023, to include after
release 2.2 -- defaults to 0->180 mappings now every time no mapping
exists.

# PT tracker doesn't work!

Go to 'model' tab in the tracker settings, and input the clip's
dimensions.

# Tracking's too slow or jumpy!

Set up the Accela filter. It has its own wiki page.

# I don't want to make a LED clip!

Then track a piece of paper as per [[aruco tracker]] wiki page.

# Keybindings ignored in games!

Game running as administrator with opentrack as regular user. Run both
as administrator or both as user.

# freetrack protocol doesn't work!

Try moving the software directly to a drive, e.g. "c:/opentrack".
Windows Vista and possibly others have issues with permissions. Can also
use one of the "c:/program files/" directories instead of the drive's
root.
