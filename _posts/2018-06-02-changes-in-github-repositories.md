---
layout: post
title:  "New firmware and changes in build process"
date:   2018-06-02 08:42:32 +0200
categories: iotkit update
---
I've started to work on some additional firmwares. Since they're not complete I changed the structure of the repositories and added branches.
Most importantly, the development branch.

My inspiration is from [this site](https://nvie.com/posts/a-successful-git-branching-model/) where Vincent explains a good aproach.

The build process has been modified slightly as well. All succesful build images are now placed in `builds` which makes it easier to locate them.
