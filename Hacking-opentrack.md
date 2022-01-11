This article describes source code layout and entry points for developers. Grab an IDE with cross-referencing support or at least <code>ctags</code>. I recommend Qt Creator 4.2+ without the Clang module.

I **heavily** recommend using an IDE or an editor with cross-referencing support (jump to function/class, find all usages). Otherwise navigating through the `opentrack` code is a real nightmare.

# Input, output, and filters

Trackers, filters, and protocols are defined as `tracker-*`, `filter-*`, and `proto-*`. They expose just a few symbols that are in turn used by plugin support code. Interfaces to be implemented by those three are included in [api/plugin-api.hpp](https://github.com/opentrack/opentrack/blob/master/api/plugin-api.hpp). The file is heavily commented.

# Core code

- To invoke opentrack plugins, include [api/plugin-support.hpp](https://github.com/opentrack/opentrack/blob/master/api/plugin-support.hpp). This is header-only, requiring no additional C++ dependencies other than Qt.
- Dependencies other than Qt are included in the [opentrack-depends](https://github.com/opentrack/opentrack-depends) repository. Clone the submodules, there are a few.
- Logic of sending data through tracker -> filter -> protocol pipeline is defined in [logic/pipeline.cpp](https://github.com/opentrack/opentrack/blob/master/logic/pipeline.cpp).
- Software logic that isn't purely user interface is defined the [logic/](https://github.com/opentrack/opentrack/tree/master/logic) directory.
- Main form of the user interface is defined in [variant/default/main-window.cpp](https://github.com/opentrack/opentrack/blob/master/variant/default/main-window.cpp). Most user interface forms are in the [gui/](https://github.com/opentrack/opentrack/tree/master/gui) subdirectory.
- State of tracking operation while it's running is contained in [logic/work.hpp](https://github.com/opentrack/opentrack/blob/master/logic/work.hpp). See also [logic/state.hpp](https://github.com/opentrack/opentrack/blob/master/logic/state.hpp) for state that persists while the software is running.
- Support for connecting configuration to user interface is contained in [options/options.hpp](https://github.com/opentrack/opentrack/blob/master/options/options.hpp).
- Migrations are for settings getting moved or changing meaning. See [migration/](https://github.com/opentrack/opentrack/tree/master/migration).

To be continued.