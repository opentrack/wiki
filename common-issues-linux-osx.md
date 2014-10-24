# There are no Linux binaries!

It's assumed Linux users are software developers, support for the
platform's provided for their convenience only.

You can provide your own unofficial binaries.

# Linux 'install' build target doesn't respect hier(7)!

This is on purpose. The project won't include that platform-specific
file system layout.

# No binaries for OSX!

No developer resources. Take care of QA yourself if OSX binaries are to
be released again in the future.

# How to contribute a tracker/protocol?

For now, copy the stuff from other tracker/protocol to a new directory,
remove the logic, and hack from there. Hook to the build in
CMakeLists.txt.

There'll be some stubs and docs in the future. If this is urgent, write
the stubs/docs yourself.
