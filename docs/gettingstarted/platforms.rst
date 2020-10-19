NEMS Linux on Single Board Computers
====================================

When choosing your hardware, general SBC comparisons are not necessarily
relevant since you will be deploying a NEMS Linux server specifically.
As an example, an ODROID-C2 vs Raspberry Pi 3 comparison will say
Raspberry Pi 3 has better support for video drivers. Well, that won't
matter to you; you're using NEMS Linux and we've pre-built the distro
for you. So because of this, it is helpful to review `the NEMS Linux
Stats page <https://nemslinux.com/stats/>`__, and `join our Discord
Server <https://discord.gg/e9xT9mh>`__ to make an educated decision.

Here are some general guidelines.

1. eMMC storage is better than an SD Card. This is a universal truth. SD
   Cards have a high failure rate whereas eMMC tends to operate with
   perceptively similar reliability to a traditional SSD. NEMS performs
   a lot of read/write operations, as you can imagine, so the more
   reliable your storage medium, the more reliable your NEMS Server.
2. More RAM means better performance. The minimum recommended RAM is 1 ,
   though 2  or higher will greatly improve performance and reliability
   of your NEMS Server.

Visit `the NEMS Linux web site <https://nemslinux.com/>`__ for a
complete list of supported platforms.

Raspberry Pi
------------

|image1|

`BUY NOW <https://cat5.tv/pi/>`__

Pine64
------

|image2|

Hardkernel ODROID XU4
---------------------

|image3|

FriendlyElec
------------

|image4|

Orange Pi
---------

|image5|

ASUS Tinker Board / S
---------------------

|image6|

ASUS Tinker Board S must be switched to Maskrom boot mode in order to
boot from SD card. The built-in eMMC is not big enough to run NEMS Linux
from.

Khadas VIM3
-----------

|image7|

You can boot from SD or USB, then install NEMS Linux to the integrated
eMMC storage by typing *sudo nems-install*

NEMS Linux Appliance
--------------------

|image8|
