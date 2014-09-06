- Tracking won't work!

Go to the 'mapping' window, look at rectangles with blue background, and ensure they have any content.

You can add a control point with left mouse button. Right button removes a control point. Existing points move by dragging with left button.

- PT tracker doesn't work!

Go to 'model' tab in the tracker settings, and input your clip's dimensions.

- Tracking's too slow or jumpy!

Set up the Accela filter. It has its own wiki page.

- There are no Linux binaries!

It's assumed Linux users are software developers, support for the platform's provided for their convenience only.

You can provide your own unofficial binaries.

- Linux 'install' build target doesn't respect hier(7)!

This is on purpose. The project won't include that platform-specific file system layout.

If this concerns you that much, move all to $prefix/libexec/opentrack, and $prefix/bin/opentrack should be a shell script executing $prefix/libexec/opentrack/opentrack "$@".

- No binaries for OSX!

No developer resources. Take care of QA yourself if OSX binaries are to be released again in the future.

- How to contribute a tracker/protocol?

For now, copy the stuff from other tracker/protocol to a new directory, remove the logic, and hack from there. Hook to the build in CMakeLists.txt.

There'll be some stubs and docs in the future. If this is urgent, write the stubs/docs yourself.