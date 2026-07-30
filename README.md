# Shuttle

A simple shortcut menu for macOS.

This is a maintained fork of [fitztrev/shuttle](https://github.com/fitztrev/shuttle), updated to build natively for Apple Silicon. It remains free and open source under the MIT License.

**Repository:** [https://github.com/dengblom-pcr/shuttle](https://github.com/dengblom-pcr/shuttle)

![How Shuttle works](https://raw.githubusercontent.com/fitztrev/shuttle/gh-pages/images/how-shuttle-works.gif)

## Installation (build from source)

Requires Xcode on an Apple Silicon Mac.

```bash
git clone https://github.com/dengblom-pcr/shuttle.git
cd shuttle

# Optional: regenerate compiled AppleScripts
./apple-scripts/compile-Terminal.sh
./apple-scripts/compile-Virtual.sh
# iTerm scripts need iTerm2 installed:
# ./apple-scripts/compile-iTermStable.sh
# ./apple-scripts/compile-iTermNightly.sh

xcodebuild -project Shuttle.xcodeproj -target Shuttle -configuration Release build
open build/Release/Shuttle.app
```

Copy `build/Release/Shuttle.app` to `/Applications` if you want.

Configure hosts in `~/.shuttle.json` (a default is created on first launch). See the [original wiki](https://github.com/fitztrev/shuttle/wiki) for config help.

## License

MIT — see [LICENSE](LICENSE).

- Original work: Copyright (c) 2013 Trevor Fitzgerald
- Modifications: Copyright (c) 2026 David Engblom

## Contributors

This project was created by [Trevor Fitzgerald](https://github.com/fitztrev). Thanks to everyone who contributed upstream:

* [Alexis NIVON](https://github.com/anivon)
* [Alex Carter](https://github.com/blazeworx)
* [bihicheng](https://github.com/bihicheng)
* [Dave Eddy](https://github.com/bahamas10)
* [Dmitry Filimonov](https://github.com/petethepig)
* [Frank Enderle](https://github.com/fenderle)
* [Jack Weeden](https://github.com/jackbot)
* [Justin Swanson](https://github.com/geeksunny)
* [Kees Fransen](https://github.com/keesfransen)
* Marco Aurélio
* [Martin Grund](https://github.com/grundprinzip)
* [Matt Turner](https://github.com/thshdw)
* [Michael Davis](https://github.com/mpdavis)
* [Morton Fox](https://github.com/mortonfox)
* [Pluwen](https://github.com/pluwen)
* Rebecca Dominguez
* [Rui Rodrigues](https://github.com/rmrodrigues)
* [Ryan Cohen](https://github.com/imryan)
* [Stefan Jansen](https://github.com/steffex)
* Thomas Rosenstein
* [Thoro](https://github.com/Thoro)
* [Tibor Bödecs](https://github.com/tib)
* [welsonla](https://github.com/welsonla)

## Credits

Shuttle was inspired by [SSHMenu](http://sshmenu.sourceforge.net/), the GNOME applet for Linux.

Also see [MLBMenu](https://github.com/markolson/MLB-Menu) and [QuickSmileText](https://github.com/scturtle/QuickSmileText) for direction on building a Cocoa status-bar app.
