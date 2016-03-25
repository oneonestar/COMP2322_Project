# Introduction
In the COMP2322 class project, you are required to setup a wireless router using Raspberry Pi. We have already prepared the following hardware for you:

* Raspberry Pi 2 Model B
* TP-LINK Archer T4U AC1200

AC1200 is a wireless dual band USB adapter which supports IEEE 802.11ac standard (5G Wifi). It uses the Realtek RTL8812AU chipset, but the mainline Linux Kernel does not support it yet. A hardware without driver will not function properly. Luckily, the open source community created a driver for everyone to use freely. We will be using the https://github.com/abperiasamy/rtl8812AU_8821AU_linux driver.

In this project, we will provide you a pre-compiled kernel module for AC1200. You only need to insert the kernel module and the operating system will be able to identify and uses the hardware.

# Insert kernel module
Type the following command:
```
# Update the Linux Kernel to a specific version
$ sudo rpi-update 692dde0c1586f7310301379a502b9680d0c104fd
$ reboot

# Download the kernel module and insert it
$ wget https://github.com/oneonestar/COMP2322_Project/raw/master/8812au.ko
$ sudo insmod 8812au.ko
```

>**Additional information**<br> If you are interested in compiling the kernel module on your own, you may refer to this article: http://www.ploxiln.net/rpi_kernel_modules.html

To verify the installation, type the command `dmesg`. You should be able to see an output message mentioning the rtl8812au driver.
```
$ dmesg
...
[ 1241.827805] usbcore: registered new interface driver rtl8812au
```

Now you may plugin your TP-LINK USB dongle. Type the command `dmesg` again to verify that the dongle is identified by the OS successfully.
```
$ dmesg
[ 3648.998209] usb 1-1.4: new high-speed USB device number 8 using dwc_otg
[ 3649.098968] usb 1-1.4: New USB device found, idVendor=2357, idProduct=0101
[ 3649.098987] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 3649.098998] usb 1-1.4: Product: 802.11n NIC
[ 3649.099007] usb 1-1.4: Manufacturer: Realtek
[ 3649.099016] usb 1-1.4: SerialNumber: 123456
[ 3650.153428] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3650.218288] cfg80211: Calling CRDA for country: HK
[ 3650.236903] cfg80211: Regulatory domain changed to country: HK
[ 3650.236964] cfg80211:  DFS Master region: unset
[ 3650.236978] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[ 3650.236998] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[ 3650.237017] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 1700 mBm), (N/A)
[ 3650.237035] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2400 mBm), (0 s)
[ 3650.237052] cfg80211:   (5490000 KHz - 5710000 KHz @ 160000 KHz), (N/A, 2400 mBm), (0 s)
[ 3650.237067] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 3000 mBm), (N/A)

```

# A Pi-based wireless router
Now you can utilize the TP-LINK USB dongle and setup your Pi-based wireless router. It is your task to figure out how to setup the router. You may refer to the following articles:
* https://learn.adafruit.com/setting-up-a-raspberry-pi-as-a-wifi-access-point/install-software
* http://raspberrypihq.com/how-to-turn-a-raspberry-pi-into-a-wifi-router/
* https://opensysnotes.wordpress.com/2015/03/16/hostapd-configuration-for-rtl8812/

Beware that the chipset for the dongle is rtl8812. The configuration may be slightly different from other generic drivers.
