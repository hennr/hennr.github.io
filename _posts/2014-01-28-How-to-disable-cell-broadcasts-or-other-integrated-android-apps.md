---
layout: post
title:  "How to disable cell broadcasts or other integrated android apps?"
categories: android
---

I recently updated my Samsung Galaxy S2 to the latest cyanogen mod 10.1.3 which unfortunately has a buggy version of cell broadcast integrated.

I receive cell broadcasts every now and then and turning them of in the options menu does not help.
So I had to find a way to disable the whole cell broadcast app…

As the cell broadcast app is integrated in the distribution you cannot uninstall or disable it.
The way I found to get rid of cell broadcasts was to remove it from the auto start list using a tool named `Autostarts`.
Autostarts is available as Free Software in the alternate [f-droid](https://f-droid.org/) app “market” and can be bought in google’s play store, too.

Once installed, open the app and browse the “After Startup” category to find the “cell broadcast” app which you then select and disable. After rebooting your device, no more cell broadcasts will bug you.
