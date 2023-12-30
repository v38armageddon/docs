# Flash the ISO

### Classic Method

After choosing a ISO, you need:

* The Vincent OS ISO
* A external device for the ISO
* Rufus (if you are on Windows)
* Enough storage space for Vincent OS
* **Backup all your personnal data in a external device and/or a cloud!**

{% hint style="warning" %}
Make sur the Secure Boot of your computer is disabled, otherwise, Vincent OS won't boot.

Check the manual page of your motherboard how to disable.
{% endhint %}

If you are on Windows:\
Download Rufus and launch from your system, chose the periphecal of your external device and select the Vincent OS ISO by clicking on the button: SELECTION, after, click on: START. Select the ISO method and wait.\
\
If you are on Linux:\
You can use GNOME Disk for flashing the ISO in your external device. It's the safest and recommented method if you don't want be risky. On GNOME Disk, select your device, click on hamburger button and select: Restore disk image. Select the Vincent OS ISO and wait (you need to enter your password before GNOME Disk start).

{% hint style="danger" %}
**All your data in you external device will be erased, make sure to backup your data!**
{% endhint %}

After flashing your devince, reboot your computer and boot on the device. Check the manual on your motherboard how to change the boot order.



***

### Ventoy Method

You can drag and drop the Vincent OS ISO into your Ventoy USB Stick, make sure you have the latest version of Ventoy to avoid problems.
