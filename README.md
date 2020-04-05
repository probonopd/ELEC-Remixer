# ELEC-Remixer

Remix AlexELEC, OpenELEC, LibreELEC, CoreELEC,...

## Motivation

* There are many different ...ELEC-based special-purpose distributions out there, e.g., LAKKA, but they are not always built for all the machines
* Building AlexELEC, OpenELEC, LibreELEC, CoreELEC,... from source code may take over 10 hours the first time, which makes it infeasible to do this on Travis CI

Hence, can we take a build that we know is working for our machine, and take its "hardware support" files and "transplant" them into the distribution we want to run?

## Use cases

AlexELEC has support for Amlogic __S805__ (even 512 MB "fake 1 GB" MXQ boxes), S812, S905 / S905X / 905D / 905W and S912. It also comes with Tvheadend

Using e.g., the S805.MXQ_V31 build from https://github.com/AlexELEC/AE-AML/releases,

* I want to have my own/more stock (non-Russian) preconfiguration (`squashfs-root/usr/share/kodi/config/`, especially `squashfs-root/usr/share/kodi/config/guisettings.xml` and `squashfs-root/usr/share/kodi/userdata/RssFeeds.xml`). Look at https://github.com/AlexELEC/AE-AML/tree/master/projects/S805/packages/kodi/patches to see what may need to be reverted
* I want to pre-bundle my own set of add-ons (`squashfs-root/usr/share/kodi/addons/`)
* I want to have LAKKA for S805.MXQ_V31
* I want to have AlexELEC but without the Russian preconfiguration

## Theory of operation

- Get built image
- Extract image
- Extract squashfs
- Make needed modifications
- Recreate squashfs
- Recreate .img.gz (for new installations) and .tar (for updating)

## Shortcut 

Even though the squashfs extraction and recompression is relatively quick, we could be even quicker by appending to the original squashfs rather than extracting it.
