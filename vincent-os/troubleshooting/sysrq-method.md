# SysRq Method

{% hint style="danger" %}
SysRq call directly in the kernel and therefore, you must not use this combination other than to solve system unresponsive problems.\
\
With a little mistake manipulation, you can loose all your unsaved work!
{% endhint %}

{% hint style="info" %}
Difficulty level:

:star::star::star:
{% endhint %}

If your system become unresponcive, you can use SysRq to perform kernel level actions to troubleshoot your system.

### Activation

By default, all versions of Vincent OS have SysRq enabled. You can verify if SysRq is activated by opening a terminal and enter this command:

Vincent OS Standard Edition:

```powershell
PS> Get-Content /proc/sys/kernel/sysrq
```

Vincent OS Legacy Edition:

```bash
$ cat /proc/sys/kernel/sysrq
```

If there is other values returned than `1`, enable the SysRq via the command:

Vincent OS All Editions:

```sh
sudo sysctl kernel.sysrq=1
```

### REISUB Method

{% hint style="info" %}
REISUB Method is a memotecnical way to troubleshoot the Operating System in case of a unresponcive system.
{% endhint %}

You can reboot your system using the REISUB Method, here's how to do it:

| Keyboard Shortcut | Description                                       |
| ----------------- | ------------------------------------------------- |
| Alt+SysRq+R       | Switch keyboard mode from RAW mode to XLATE mode. |
| Alt+SysRq+E       | Send SIGTERM to all processes (except init).      |
| Alt+SysRq+I       | Send SIGKILL to all processes.                    |
| Alt+SysRq+S       | Sync all data to disk.                            |
| Alt+SysRq+U       | Unmount and remount all filesystems to read-only. |
| Alt+SysRq+B       | Reboot.                                           |

More informations can be found on ArchLinux wiki and Wikipedia:

{% embed url="https://wiki.archlinux.org/title/Keyboard_shortcuts#Kernel_(SysRq)" %}
Keyboard Shortcut
{% endembed %}

{% embed url="https://en.wikipedia.org/wiki/Magic_SysRq_key#Commands" %}
Magic SysRq key
{% endembed %}
