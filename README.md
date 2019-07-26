# QEMUDebianPPE64Image

This is an image of a 64-bit Debian installed in QEMU for debugging PPC-systems on x86-64 hardware.

## How to split the file

> tar -cvjf debian.tar.bz2 debian.img

> split -b 10M home.tar.bz2 "debian.img.tar.bz2.part"

## How to extract this

Due to the limit of 100MB per file on GitHub, I splitted the file into several single files that first
need to be combined again.

> cat debian.img.tar.bz2.part* > debian.img.tar.gz.joined

> tar -zxvf debian.img.tar.gz.joined

## How to run this

Run this with

> export HDD=debian.img         # The extracted HDD image file

> export CDROM=any_cdrom.iso    # Choose any ISO file you want or leave out the CD-Rom part completly

> export MEMORY=1024            # Choose the amount of Memory in MB

> qemu-system-ppc64 -hda $HDD -boot d -cdrom $CDROM -m $MEMORY

## Username and password

Since this is for local testing only, security was no concern. So, the username and password is 

> test

and 

> test

again. Also, the root password is 

> test
