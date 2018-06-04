---
layout: post
title:  "New firmware and changes in build process"
date:   2018-06-02 08:42:32 +0200
categories: iotkit update
---
I've started to work on some additional firmwares. Since they're not complete I changed the structure of the repositories and added branches.
Most importantly, the development branch.

## Github changes
My inspiration is from [this site](https://nvie.com/posts/a-successful-git-branching-model/) where Vincent explains a good approach.

Development is now done in the development branch (of course).

The build process has been modified slightly as well. All successful build images are now placed in `builds` which makes it easier to locate them.

## Firmware changes
A new firmware is on its way. This time it's with a small OLED display allowing students to provide information (such as values) in a convenient location

## Build changes
Platformio allows to invoke extra scripts in the build process. I use a python script to move the `firmware.bin` files to a common `builds` directory instead of leaving them in the default `.pioenvs` directory. This makes it easier to locate and upload the firmware.
