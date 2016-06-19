This article describes source code layout and entry points for developers. Grab an IDE with cross-referencing support or at least <code>ctags</code>.

- Dependencies other than Qt are included in the [opentrack-depends](https://github.com/opentrack/opentrack-depends) repository.
- Main form of the user interface is defined in [facetracknoir/ui.cpp](https://github.com/opentrack/opentrack/blob/unstable/gui/ui.cpp)
- Software logic that isn't purely user interface is defined in [opentrack-logic/](https://github.com/opentrack/opentrack/tree/unstable/opentrack-logic)
- Logic of sending data through tracker -> filter -> protocol pipeline is defined in [opentrack/tracker.cpp](https://github.com/opentrack/opentrack/blob/unstable/opentrack-logic/tracker.cpp)
- To invoke opentrack plugins, include [opentrack/plugin-support.hpp](https://github.com/opentrack/opentrack/blob/unstable/opentrack/plugin-support.hpp). This is header-only, requiring no additional C++ dependencies other than Qt.
- Trackers, filters, and protocols are defined as ftnoir_tracker_\*, ftnoir_filter_\* and ftnoir_protocol_\*. They expose just a few symbols that are in turn used by plugin support code. Interfaces to be implemented by those three are included in [opentrack/plugin-api.hpp](https://github.com/opentrack/opentrack/blob/unstable/opentrack/plugin-api.hpp)
- Support for connecting configuration to user interface is contained in [opentrack-compat/options.hpp](https://github.com/opentrack/opentrack/blob/unstable/opentrack-compat/options.hpp)
- State of tracking operation while it's running is contained in [opentrack-logic/work.hpp](https://github.com/opentrack/opentrack/blob/unstable/opentrack-logic/work.hpp). See also [opentrack-logic/state.hpp](https://github.com/opentrack/opentrack/blob/unstable/opentrack-logic/state.hpp) for state that persists while the software is running.

To be continued.