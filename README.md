# debos-braveheart
A set of [debos](https://github.com/go-debos/debos) recipes to build a custom GNU/Linux [Debian](https://www.debian.org) image for the [Pine64 PinePhone Braveheart](https://wiki.pine64.org/index.php/PinePhone).

It's a fork of [Arnaud Ferraris' project: debos-pinephone](https://gitlab.com/a-wai/debos-pinephone).

This different branch was born upon personal specific needs, but maybe could be useful for others. Any feedback, suggestion, bug report or help is welcome.

# Main Feature

This image is
- Based on GNU/Linux Debian 11 codename "Bullseye" (aka testing)
- Include few useful command-line utilities: wget, nano

# Changes from Arnaud's version:

- [edited rootfs.yaml] changed target Debian OS from Sid (aka unstable) to "Bullseye" (aka testing) 
- [edited rootfs.yaml] changed hostname from "pinephone" to "braveheart" as PINE64 will release different pinephone models
- [edited setup-users.sh] changed the default root password to "toor"  
- [added overlay] new file /etc/apt/sources.list including bullseye-backports (main, contrib, non-free) and bullseye-security (main, contrib, non-free) 
- [removed image.yaml] removed packages: gnome-2048, gnome-chess, chatty, kgx
- [removed rootfs.yaml] removed [User applications]: cheese, youtube-dl, lollypop, gnome-maps
- [added rootfs.yaml] added [Console applications]: nano
- [edited rootfs.yaml] replaced "Epiphany" web browser with "Firefox ESR" as default browser
- [edited image.yaml] changed default username from "debian" to "user"
- [added image.yaml] added packages: gnome-terminal

# Default login
The default user is `user` with password `1234`.
The default `root` password is `toor`.

## Build

To build the image, you need to have `debos` and `bmaptool`. On a debian-based
system, install these dependencies by typing the following command in a terminal:

```
sudo apt-get install debos bmap-tools
```

Then simply browse to the `debos-braveheart` folder and execute `./build.sh`.

## Install

Insert a MicroSD card into your computer, and type the following command:

```
sudo bmaptool copy debian-pinephone-braveheart.img /dev/<sdcard>
```

or:

```
sudo dd if=debian-pinephone-braveheart.img of=/dev/<sdcard> bs=1M
```

*Note: Make sure to use your actual SD card device, such as `mmcblk0` instead of
`<sdcard>`.*

**CAUTION: This will format the SD card and erase all its contents!!!**

## Included software

The generated image include, among others, the following packages:

- [Clocks](https://source.puri.sm/Librem5/gnome-clocks) application
- [Settings](https://source.puri.sm/Librem5/gnome-control-center) application
- [Usage](https://source.puri.sm/Librem5/gnome-usage), a system monitor
- [Squeekboard](https://gitlab.com/a-wai/squeekboard) virtual keyboard

Please, check Arnaud Ferraris' [README.md](https://gitlab.com/a-wai/debos-pinephone/-/blob/master/README.md) about further details on packages built from upstream sources, on packages built from third-party-modified sources, on packages built from modified sources, what works and what doesn't. 
