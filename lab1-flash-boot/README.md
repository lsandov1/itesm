First Boot
==========

Goal
----

Download an already create image, flash it and boot a system

HW Requisites
-------------

* Humming Board
* mini SD Card

SW Requisites
-------------

* Linux Host (Ubuntu, Debian, OpenSUSE, etc) running natively or virtually

Steps
-----

# Image name and URL
    
    $ IMAGE="debian-jessi-4-july-2014.img"
    $ IMAGE_XZ="$IMAGE.xz"
    $ IMAGE_URL="http://download.solid-run.com/pub/solidrun/cubox-i/Debian/Jessi-repackaged-trial/$IMAGE_XZ"

# Create a specific folder for humming data

    $ mkdir -p ~/humming_board
    $ cd ~/humming_board

# Get the image

    $ wget $IMAGE_URL

# Insert the SD and identify which node device was created, and unmount it

    $ dmesg | tail
    $ sudo umount /dev/sdb* # In case /dev/sdb device was created

# Decompress the image and flash it to the SD

    $ xz -d $IMAGE_XZ
    $ sudo dd if=$IMAGE of=/dev/sdb bs=4M
    $ sync

# Place the mini-SD into the board and power it.
