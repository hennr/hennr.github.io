---
layout: post
title:  "How to remove HDMI Sound cards under Linux"
categories: linux
---

I lately ran into a configuration hell regarding Linux and sound.
And as if it’s not bad enough to fight against pulse and alsa my Nvidia sound card showed up to even make the mess worse.

So I decided to kick pulse, install alsa only and remove the Nvidia sound card to only keep my mainboard’s sound card and alsa.

This solution works like a charm.
All applications choose the correct sound card by default now.

OK, so what should I do?


First, find your card’s id running:

```sh
lspci | grep -i audio
```

Something like this should appear:

```
02:00.1 Audio device: Nvidia Corporation High Definition Audio Controller (rev a1)
```

Where “02:00.1” is the id we are looking for.
Now let’s find the matching pseudo file in /sys:

```sh
find /sys/devices -name *02:00.1
```

Something like this should show up now:

```
/sys/devices/pci0000:00/0000:00:02.0/0000:02:00.1
```

Bingo, the last thing to do is telling our kernel not to enable this hardware on boot.
Add the following entry to your /etc/rc.local and and reboot your system.

```
echo 1 > /sys/devices/pci0000:00/0000:00:02.0/0000:02:00.1/remove
```

**Note**: you need to choose your own path of course.

That’s it, enjoy your system with sound.
