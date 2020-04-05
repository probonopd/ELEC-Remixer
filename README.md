# ELEC-Remixer

Remix AlexELEC, OpenELEC, LibreELEC, CoreELEC,...

## Motivation

* There are many different ...ELEC-based special-purpose distributions out there, e.g., LAKKA, but they are not always built for all the machines
* Building AlexELEC, OpenELEC, LibreELEC, CoreELEC,... from source code may take over 10 hours the first time, which makes it infeasible to do this on Travis CI

Hence, can we take a build that we know is working for our machine, and take its "hardware support" files and "transplant" them into the distribution we want to run?

## Use cases

* I want to have LAKKA for S805.MXQ_V31
* I want to have AlexELEC but without the Russian preconfiguration
* I want to pre-bundle my own set of add-ons and preconfiguration

## Theory of operation

- Get built image
- Extract image
- Extract squashfs
- Make needed modifications
- Recreate squashfs
- Recreate .img.gz (for new installations) and .tar (for updating)
