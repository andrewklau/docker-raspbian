raspbian
===================

[Raspbian](http://www.raspbian.org/) image for docker on raspberry pi. Raspbian version 2016-09-03-raspbian-jessie-minbase


Generating
----------

This image is built on a raspberry pi running raspbian. A chroot is created using debootstrap and compressed so docker can add the root filesystem during the build process. The compression requires xz-utils (or something similar) to be installed on the build machine.  

[mkimage-raspbian.sh](https://github.com/sdhibit/docker-rpi-raspbian/blob/master/mkimage-raspbian.sh) is used to build and configure the chroot. This script **heavily** borrows from docker's [mkimage.sh](https://github.com/docker/docker/blob/master/contrib/mkimage.sh) script.

Building
--------
If you want to build this image yourself, run the following to generate the compressed chroot.

```bash
$ rm *.tar.xz
$ apt-get install debootstrap
$ ./mkimage-raspbian.sh
```
Get lots of tacos.

```bash
$ docker build -t rpi-raspbian .
```

Running
-------
This image does not do anything fancy, but if you want to test it out, run the following:

```bash
$ docker run --name raspbian -it andrewklau/rpi-raspbian:latest /bin/bash
```
