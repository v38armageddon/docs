# Post Installation Tips
Congratulations! You have successfully installed Vincent OS and are now ready to explore its features! To avoid getting lost in this new operating system, follow these tips.

## Desktop Environment
You can see that the desktop environment is different from what you may be used to. Take some time to explore the new layout and features. Here are a few key points to help you navigate:

### Top bar
The top bar contains three icons, on the left you will have the date and time click here and you have the calendar.

In the center you have the list of the notifications you have missed and on the right, you have the user menu.\
The user menu allows you to switch between different user accounts and access to system shutdown options.

### Bottom bar
The bottom bar contains three elements: the start menu on the left, allowing you to access your applications, the taskbar in the center, showing your open applications, and the system tray on the right, displaying quick settings.

----
## Discover (Software Center)
The Discover Software is the software store for Vincent OS, allowing you to easily find, install, and manage installed software.

If you are more of a technical user, you can also use the command line to install software packages with ``pacman``.

```admonish warning
Vincent OS is based on Arch, which means you can take advantage of the Arch User Repository (AUR) for additional software packages.

We don't recommend using AUR packages unless you are sure of what you are doing, as they are not officially supported and may cause system instability.

We offer the possibility to install ``yay`` on the official Vincent OS Repository, an AUR helper but we are not responsible for any issues that may arise from using AUR packages.
```

## Updates
When you have a fresh install of Vincent OS, some packages may be outdated. To ensure you have the latest software and security updates, it's a good idea to run the following commands:
```powershell
Update-System.ps1
```
This script will update your system and install any available updates.

## Core LivePatch
Vincent OS includes a unique feature called Core LivePatch, allows you to update critical system components without rebooting your machine.

To get more technical details about how Core LivePatch works and how to use it, please refer to the [Core LivePatch documentation](../core-livepatch.md).