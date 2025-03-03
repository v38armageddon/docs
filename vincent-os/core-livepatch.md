# Core LivePatch

{% hint style="warning" %}
Not to be confused with Kernel Livepatching and Livepatch, a method to Livepatch the Linux Kernel (see: [https://wiki.archlinux.org/title/Kernel\_live\_patching](https://wiki.archlinux.org/title/Kernel_live_patching), [https://www.kernel.org/doc/html/latest/livepatch/livepatch.html](https://www.kernel.org/doc/html/latest/livepatch/livepatch.html))
{% endhint %}

{% hint style="warning" %}
This section only apply on the following edition: Vincent OS Standard
{% endhint %}

### Definition

Core LivePatch (abbreviated to CLP) allows you to update critical Vincent OS part via patches without rebooting your computer.

### Features

Core LivePatch can do the following tasks:

* **Applying critical patches**: Update key system files, such as configuration files in `/etc`, to address urgent issues.
* **Revert a previous version of a specific package**: Roll back a specific package version to resolve critical issues (e.g. Revert a previous version for the following issue: [nvidia-black-screen-after-an-update.md](troubleshooting/nvidia-black-screen-after-an-update.md "mention")).

All patches are distributed in a `.clp` format, designed specifically for Vincent OS.

{% hint style="success" %}
If necessary, you can rollback a Core LivePatch update if some file / package break your system.
{% endhint %}
