---
title: "Cyanogen Mod 7 – Android 2.3.3 Gingerbread"
date: 2011-04-24 18:26:24 +0200
tags:
  - android
---

It has been a long time since the announcement of Gingerbread, last year in December, and still no official update for our phones here in Europe. I definitely want to test the [NativeActivity I've spoken before](http://www.srombauts.fr/2011/03/01/android-2-3-nativeactivity/), and I would like to get root access on my phone to go further in my testing (and update relative posts on this blog).

So yesterday evening I made the big jump to bring to my Nexus One the power of the recently released [Cyanogen Mod 7](http://www.cyanogenmod.com/). I just followed the provided [wiki tutorial to update the Nexus One](http://wiki.cyanogenmod.com/index.php?title=Nexus_One:_Full_Update_Guide), but here is my experience about it.

![CyanogenMod Logo](/assets/images/cyanogen_logo.png)

So I started by backuping my data: SMS with [SMS Backup & Restore](http://market.android.com/details?id=com.riteshsahu.SMSBackupRestore), log calls with [Call Log Backup & Restore](http://market.android.com/details?id=com.riteshsahu.CallLogBackupRestore), [Dolphin Browser HD](https://market.android.com/details?id=mobi.mgeek.TunnyBrowser) links with the [Bookmarks to SD plug-in](https://market.android.com/details?id=mobi.mgeek.BookmarkPlugin), and some savegames, that I all copied from my SD Card to my computer hard drive (given that other important data like Contacts, Email, Calendar and GTasks are already synchronized by Google). I forgot to save my pictures…

Then I unmounted and formated the SD Card, rebooted to the bootloader to wipe all data and restore factory settings.

I installed fastboot on my SDK tools directory, and unlocked my bootloader with:
`fastboot oem unlock`

I first wanted to flash the ClockworkMod 3.0.0.5 recovery for later use with the famous [ROM Manager application](https://market.android.com/details?id=com.koushikdutta.rommanager), but this version failed to unpack the radio-image I had to flash before Cyanogen (for script compatibility error), so I fall back on the **Amon_Ra's Recovery** manual method.
`fastboot flash recovery /path/to/recovery-RA-nexus-v2.1.1-CM.img`

I had no more trouble flashing the radio-image (passion.5.08.00.04.zip), and then the cyanogen-mod7-update (update-cm-7.0.0-N1-signed.zip) and the Google applications (gapps-gb-20110307-signed.zip). I had to wipe all data once more to boot into the new OS, but after I have been able to restore all my data, to re-download all my favorite applications. Now I can enjoy the new eye-candy tools and other gadgets from Cyanogen, I can play with the new Java and Native API or improvement from Gingerbread, and I can use "root enabled application" like ROM Manager or the "su" command line tool.

This morning, I add the good surprise to see that a ROM update was out, so I used successfully the ROM Manager application to make a full backup of my phone to the SD Card (need to reboot on ClockworkMod recovery to proceed, 350Mo written in a few minutes), to download and to flash the OS update. Quick and smooth.

So now on, stay tuned for more tips and tricks about Android development!
