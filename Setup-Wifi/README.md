# Wifi Setup for myRIO

The following instruction describes how to setup wifi for the nanins equipped with a myRIO using a [dongle](http://www.hardkernel.com/main/products/prdt_info.php?g_code=G137447734369).


## Instruction: Wifi on myRIO

1. Connect over SSH to the linux of the myRIO. When connecting via USB the IP-address is: `172.22.11.2`
2. Create the folder for the dongle firmware: `mkdir /lib/firmware/rtlwifi`
3. Copy (e.g. scp) the firmware file [rtl8192cufw_TMSC.bin](rtl8192cufw_TMSC.bin) to the created folder
4. When you plug-in the dongle, the firmaware should be loaded correctly. Check with `dmesg`
5. Unblock wifi from rfkill: `rfkill unblock wifi`
6. Startup wifi: `ifconfig wlan0 up`. Check if wlan0 is up with `ìfconfig`
7. Connect via the browser to the myRIO using the IP. Under *Netzwerkeinstellungen* the wlan0 should be available!
8. Select the connection to the correct network (see instruction below) using a *static IP* with the following addresses:

   - IPv4: **172.22.22.2**
   - Subnetmask: **255.255.255.0**
   - Gateway: **172.22.22.1**

9. The myRIO is ready!


Help for the myRIO/Wifi-Dongle Setup was found in [this NI-Community forum thread](https://decibel.ni.com/content/thread/31019).


## Instruction: Setup Router

Setup a router for the Nanins network using the following settings:

- Network-Name: **nanins-'name'** (e.g. nanins-marlin)
- Password: **naninsPWD**
- Router-IP: **172.22.22.1**
- Subnetmask: **255.255.255.0**
- IP-Range: **172.22.22.2-xxx**