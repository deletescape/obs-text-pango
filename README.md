Text Source using Pango for OBS Studio
======================================

This plugin provides a text source for OBS Studio. The text is layed out
and rendered using Pango.

Current Features
----------------

* Text alignment
* Text color
  * Colors for top and bottom of the text to create gradients
* Outline
  * Configurable width of the outline
  * Configurable color of the outline
* Drop Shadow
  * Configurable offset of the drop shadow from the text
  * Configurable color for the drop shadow
* Vertical Text
* Per Line gradients
* Read from file
  * Chat log mode (Last X lines from file)
  * Reload on changes
* Opacity

Considering Features
----------------
* Custom text width
  * Vertical Text Align
  * Word wrapping

Build
-----

You can either build the plugin as a standalone project or integrate it
into the build of OBS Studio (untested).

Building it as a standalone project follows the standard cmake approach.
Create a new directory and run 
```bash
cmake ... <path_to_source>
	-DCMAKE_INSTALL_PREFIX=<path_to_deps_dir>
	-DOBS_DIR=<path_to_obs>
```
for whichever build system you use (only ninja tested). You may also set
the `OBS_DIR` environment variable to the location of the OBS source tree.
Depending on the name of your obs build dir adjust `PATH_SUFFIXES`
appropriately.

If the include cmake find modules fail to find packages on your system
please submit a PR with appropriate `NAMES` to find them on your platform.

To integrate the plugin into the OBS Studio build put the source into
the `plugins/obs-text-pango` folder of OBS Studio source and add it to the
`plugins/CMakeLists.txt`.

Linux
-----
On Debian and its derivitaves you can install `libpango1.0-dev` for all the build time dependencies. Everywhere else its typically just `pango`.

For precompiled binaries extract to `~/.config/obs-studio/plugins` and ensure dependencies are installed.

Windows
-----
You will have to build the toolchain yourself, but it should be simplified if you have a posix shell environment such as cygwin and the visual studio build tools via https://github.com/kkartaltepe/pango-win32-build

Install by extracting into your obs studio folder' `obs-plugins`

Mac
-----
Install pango via `brew install pango` and you should be set.
