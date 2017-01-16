---
layout: post
title:  "Erasing files and folders recursively under Linux"
categories: linux
---

I lately needed to erase some documents from a hard drive to make sure the person I sold this HDD could read / restore the files any more.

I remembered that the tool `shred` will do the job by writing over the files with garbage several times.

The problem I encountered is that shred has no option to do that recursively, it will only work for single files but not for folders.
I browsed the net and found the solution:

    find name_of_folder_to_trash -type f -exec shred ‘{}’ \;
    rm -rf name_of_folder_to_trash

Ugly and hard to remember, right?

The better way is to use a tool which has a switch to run recursively. This is where `wipe` comes in.

    wipe -r name_of_folder_to_trash

Happy shredding, eh wiping :)
