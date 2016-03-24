# Introduction

In COMP2322 class project, you are required to setup a wireless router using Raspberry Pi. We have already prepared the following hardware for you:

* Raspberry Pi 2 Model B+
* TP-LINK Archer T4U AC1200

AC1200 is a wireless dual band USB adapter which supports IEEE 802.11ac standard (5G Wifi). It uses the Realtek RTL8812AU chipset, but the mainline Linux Kernel does not have support yet. A hardware without driver will not work properly. Luckily, the open source community created a driver for everyone to use freely.

In this project, we will provide you a pre-compiled kernel module for AC1200. You only need to insert the kernel module and the operating system will be able to identify and uses the hardware.

# Insert Kernel Module
Type the following command:
$ sudo rpi-update 692dde0c1586f7310301379a502b9680d0c104fd
