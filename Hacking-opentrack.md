This article describes source code layout and entry points for developers. Grab an IDE with cross-referencing support or at least <code>ctags</code>.

- Main form of the user interface is defined in [facetracknoir/ui.cpp](https://github.com/opentrack/opentrack/blob/unstable/facetracknoir/ui.cpp)
- Software logic that isn't purely user interface is defined in [opentrack/](https://github.com/opentrack/opentrack/tree/unstable/opentrack)
- Logic of sending data through tracker -> filter -> protocol pipeline is defined in [opentrack/tracker.cpp](https://github.com/opentrack/opentrack/blob/unstable/opentrack/tracker.cpp)
- To invoke opentrack plugins, include [opentrack/plugin-support.hpp](https://github.com/opentrack/opentrack/blob/unstable/opentrack/plugin-support.hpp). This is header-only, requiring no additional C++ dependencies other than Qt.
- Trackers, filters, and protocols are defined as ftnoir_tracker_\*, ftnoir_filter_\* and ftnoir_protocol_\*. They expose just a few symbols that are in turn used by plugin support code. Interfaces to be implemented by those three are included in [opentrack/plugin-qt-api.hpp](https://github.com/opentrack/opentrack/blob/unstable/opentrack/plugin-qt-api.hpp)
- Support for connecting data to user interface is contained in [opentrack/options.hpp](https://github.com/opentrack/opentrack/blob/unstable/opentrack/options.hpp)
- State of tracking operation while it's running is contained in [opentrack/work.hpp](https://github.com/opentrack/opentrack/blob/unstable/opentrack/work.hpp). See also [opentrack/state.hpp](https://github.com/opentrack/opentrack/blob/unstable/opentrack/state.hpp) for state that persist while the software is running.

To be continued.