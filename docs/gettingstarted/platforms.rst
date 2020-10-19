Available Platforms
====================

NEMS Linux on Single Board Computers
-------------------------------------

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

NEMS Linux Docker Container
===========================

The NEMS Linux Docker Container is coming soon. It is currently
in *heavy testing*. If you decide to try it, please do not do so in a
production environment, and be sure to report any issues on our Discord
server.

Install NEMS Linux for Docker
-----------------------------

Basic Installation
~~~~~~~~~~~~~~~~~~

This command will launch a new Docker container called *nemslinux* using
default settings:

docker run --hostname nems --mount
type=tmpfs,destination=/tmp,tmpfs-mode=1777 --mount
type=tmpfs,destination=/var/www/html/backup/snapshot,tmpfs-mode=1770
--restart=unless-stopped --stop-timeout 120 --name nemslinux -d
baldnerd/nemslinux:1.6_build1

Install NEMS Linux Docker Container on a Physical Network
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Docker is unlike a standard deployment since by default (with a basic
install) only the host computer will have access to it. That of course
is not ideal for a NEMS Linux server if you wish to be able to
administer it from multiple systems, view dashboards, or use a NEMS
Warning Light.

While NEMS Linux will function fine on a Docker network (eg.,
172.17.0.2), if you wish to have full access to your NEMS Server just as
you would with a physical appliance, you will need to connect it to your
physical network.

The two most common options for specifying a network is to use either
DHCP or a Static IP Address:

Using DHCP
^^^^^^^^^^

docker run --network=multi-host-network --hostname nems --mount
type=tmpfs,destination=/tmp,tmpfs-mode=1777 --mount
type=tmpfs,destination=/var/www/html/backup/snapshot,tmpfs-mode=1770
--restart=unless-stopped --stop-timeout 120 --name nemslinux -d
baldnerd/nemslinux:1.6_build1

Using Static IP
^^^^^^^^^^^^^^^

Change the sample 10.0.0.105 IP address to suit your needs.

docker network connect --ip 10.0.0.105 multi-host-network run --hostname
nems --mount type=tmpfs,destination=/tmp,tmpfs-mode=1777 --mount
type=tmpfs,destination=/var/www/html/backup/snapshot,tmpfs-mode=1770
--restart=unless-stopped --stop-timeout 120 --name nemslinux -d
baldnerd/nemslinux:1.6_build1

Please see `Docker's Network Connections
documentation <https://docs.docker.com/engine/reference/commandline/network_connect/>`__ for
more help.

With USB Support
~~~~~~~~~~~~~~~~

To connect a USB device such
as `temper <https://docs.nemslinux.com/hardware/temper>`__ to your
Docker-based NEMS Server, first determine its /dev assignment on your
host, and then run NEMS as follows, replacing ttyUSB0 with your actual
USB device:

docker run --device=/dev/ttyUSB0 --hostname nems --mount
type=tmpfs,destination=/tmp,tmpfs-mode=1777 --mount
type=tmpfs,destination=/var/www/html/backup/snapshot,tmpfs-mode=1770
--restart=unless-stopped --stop-timeout 120 --name nemslinux -d
baldnerd/nemslinux:1.6_build1

Initialize Your Docker-Based NEMS Server
----------------------------------------

Initializing a NEMS Server within a Docker Container is different than
all other platforms.

On the Docker host, simply run:

docker exec -it nemslinux nems-init

Access NEMS Linux CLI
---------------------

Should you have need to access the NEMS Linux CLI, you may do so by
launching *bash* in your container.

docker exec -it nemslinux bash
