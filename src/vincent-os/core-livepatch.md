# Core LivePatch
```admonish warning
Not to be confused with Kernel Livepatching and kpatch, (see: [https://wiki.archlinux.org/title/Kernel\_live\_patching](https://wiki.archlinux.org/title/Kernel_live_patching), [https://www.redhat.com/fr/blog/introducing-kpatch-dynamic-kernel-patching](https://www.redhat.com/fr/blog/introducing-kpatch-dynamic-kernel-patching))
```

## Definition
Core LivePatch (abbreviated to CLP) allows you to update critical Vincent OS part via patches without rebooting your computer.

```admonish note
An automated ``systemd service`` runs on the background to manage the update and apply all patches. It runs all days at 12H00 (24h format).

You can disable this service by running the following command:\
`systemctl disable core-livepatch-update.timer`
```

## Features
Core LivePatch can do the following tasks:

* **Applying critical patches**: Update key system files, such as configuration files in `/etc`, to address urgent issues.
* **Revert a previous version of a specific package**: Roll back a specific package version to resolve critical issues (e.g. Revert a previous version for the following issue: [nvidia-black-screen-after-an-update.md](troubleshooting/nvidia-black-screen-after-an-update.md "mention")).

All patches are distributed in a `.clp` format, designed specifically for Vincent OS.

```admonish info
If necessary, you can rollback a Core LivePatch update if some file / package break your system.
```

## Comparison with other live patching solutions
This is a list of live partching solutions and their key differences:
| Feature | Core LivePatch | kpatch | Canonical Livepatch |
|---------|----------------|--------|---------------------|
| Kernel Patch |  ❌ |  ✅ |  ✅ |
| Patch system configuration files |  ✅ |  ❌ |  ❌ |
| Revert patch |  ✅ |  ⚠️ |  ⚠️ |
| Supported OS |  Vincent OS |  RHEL / CentOS |  Ubuntu |
| Portability |  ⚠️ PowerShell only |  ❌ |  ❌ |
| Does not require a reboot |  ✅ |  ✅ |  ✅ |

----
Source code of Core LivePatch can be found in the [Vincent OS GitHub repository](https://github.com/Vincent-OS/clpctl).