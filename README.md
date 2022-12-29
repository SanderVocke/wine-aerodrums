# wine-aerodrums

Arch PKGBUILD for installing an additional Wine alongside the system Wine specifically for running Aerodrums.

## Disclaimer

Use at your own risk. Although this should cleanly install without touching any of your existing Wine configuration, I am not an experienced packager and do not take responsibility for any issues. Know that it installs a udev rule and a kernel module blacklist.

## Background

Aerodrums needs functioning access to the PSEye USB camera. This can be achieved using [libusb-wine](https://github.com/stanson-ch/libusb-wine) on Wine 5. Later versions of Wine do not seem to support this anymore. This package will install Wine 5 into your `/opt` folder as `wine-aerodrums` with the needed modifications for USB access to the camera. Shortcuts such as `wine-aerodrums`, `winecfg-aerodrums` etc. are installed to use this Wine installation directly.

## Usage

* Install the package.
* Reboot to make sure the Linux camera driver `gspca_ov534` for the PSEye is not loaded (can also be unloaded manually instead of rebooting)
* Plug in the PSEye camera.
* Make a new wine prefix and install aerodrums inside it using `wine-aerodrums`: `WINEPREFIX=~/.my_aerodrums_wine_prefix wine-aerodrums path-to-aerodrums-installer.exe`
* The installer should detect your camera without issues.
* To run Aerodrums: `WINEPREFIX=~/.my_aerodrums_wine_prefix wine-aerodrums "~/.my_aerodrums_wine_prefix/drive_c/Program Files (x86)/Aerodrums/aerodrums.exe"

## Audio / MIDI

Configuring audio and/or MIDI output from Aerodrums is not in the scope of this README. There are options such as using winepulse.drv, winealsa.drv or WINEASIO for audio. For MIDI, a good option is to output to your MIDI through port. The MIDI signal can then be connected to any Linux application from the through port.

## Background

All credits go to Aerodrums forum user InTheWorks: [see here](https://aerodrums.com/forums/viewtopic.php?f=9&t=35188&sid=e7e6b6a268c9e09f340cb7ad9b6aef4f).
