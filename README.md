# debos-braveheart
A set of [debos](https://github.com/go-debos/debos) recipes to build a custom GNU/Linux [Debian](https://www.debian.org) image for the [Pine64 PinePhone Braveheart](https://wiki.pine64.org/index.php/PinePhone).

It's a fork of [Arnaud Ferraris' project: debos-pinephone](https://gitlab.com/a-wai/debos-pinephone).

This different branch was born upon personal specific needs, but maybe could be useful for others. Any feedback, suggestion, bug report or help is welcome.

# Main changes from Arnaud's version:

- Based on GNU/Linux Debian 11 codename "Bullseye" (aka testing)
- Updated /etc/apt/sources.list including bullseye-backports (main, contrib, non-free) and bullseye-security (main, contrib, non-free)
- removed from image.yaml: gnome-2048, gnome-chess, chatty 
- removed from rootfs.yaml: cheese [User applications], youtube-dl [User applications], lollypop [User applications], gnome-maps [User applications]
- added to rootfs.yaml: nano [Console applications]

# Default login
The default user is `user` with password `1234`.
The default `root` password is `toor`.

## Build

To build the image, you need to have `debos` and `bmaptool`. On a debian-based
system, install these dependencies by typing the following command in a terminal:

```
sudo apt install debos bmap-tools
```

Then simply browse to the `debos-pinephone` folder and execute `./build.sh`.

## Install

Insert a MicroSD card into your computer, and type the following command:

```
sudo bmaptool copy debian-pinephone.img /dev/<sdcard>
```

or:

```
sudo dd if=debian-pinephone.img of=/dev/<sdcard> bs=1M
```

*Note: Make sure to use your actual SD card device, such as `mmcblk0` instead of
`<sdcard>`.*

**CAUTION: This will format the SD card and erase all its contents!!!**

## Included software

The generated image include, among others, the following packages:

- [Epiphany](https://gitlab.gnome.org/GNOME/epiphany) web browser
- [King's Cross](https://gitlab.gnome.org/ZanderBrown/kgx), a terminal emulator
- [Clocks](https://source.puri.sm/Librem5/gnome-clocks) application
- [Settings](https://source.puri.sm/Librem5/gnome-control-center) application
- [Usage](https://source.puri.sm/Librem5/gnome-usage), a system monitor
- [Squeekboard](https://gitlab.com/a-wai/squeekboard) virtual keyboard

Please, check Arnaud Ferraris' [README.md](https://gitlab.com/a-wai/debos-pinephone/-/blob/master/README.md) about further details on packages built from upstream sources, on packages built from third-party-modified sources, on packages built from modified sources, what works and what doesn't. 

