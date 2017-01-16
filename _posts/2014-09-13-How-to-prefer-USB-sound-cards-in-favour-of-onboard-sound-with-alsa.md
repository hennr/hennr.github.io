---
layout: post
title:  "How to prefer USB sound cards in favour of on-board sound with alsa"
categories: linux
---

Plugging in an USB sound card to a linux machine can be quite frustrating because it does not become the default device automatically.
Today I read about such an option in alsa that I didn’t know about before.

All you have to do is to open the /etc/modprobe.d/alsa-base.conf as root and toggle out a line.

Looks for this section...

    # Keep snd-usb-audio from beeing loaded as first soundcard
    options snd-usb-audio index=-2

...and make it look like this:

    # Keep snd-usb-audio from beeing loaded as first soundcard
    # options snd-usb-audio index=-2

After a reboot your USB sound card is the default card for alsa when plugged in.
