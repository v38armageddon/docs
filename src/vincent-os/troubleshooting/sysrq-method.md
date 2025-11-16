# SysRq Method

```admonish danger
SysRq call directly in the kernel and therefore, you must not use this combination other than to solve system unresponsive problems.

With a little mistake manipulation, you can loose all your unsaved work!
```

```admonish info
Difficulty level: ⭐⭐⭐
```

If your system become unresponcive, you can use SysRq to perform kernel level actions to troubleshoot your system.

### Activation
You can verify if SysRq is activated by opening a terminal and enter this command:

```powershell
Get-Content /proc/sys/kernel/sysrq
```

If there is other values returned than `1`, enable the SysRq via the command:

```sh
sysctl kernel.sysrq=1
```

### REISUB Method

```admonish info
REISUB Method is a memotecnical way to troubleshoot the Operating System in case of a unresponcive system.
```

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
- [ArchLinux Wiki Keyboard Shortcut](https://wiki.archlinux.org/title/Keyboard_shortcuts#Kernel_(SysRq))
- [Wikipedia Magic SysRq key](https://en.wikipedia.org/wiki/Magic_SysRq_key#Commands)