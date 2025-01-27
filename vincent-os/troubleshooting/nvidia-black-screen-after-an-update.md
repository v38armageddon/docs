# NVIDIA: Black screen after an update

{% hint style="info" %}
Difficulty level:&#x20;

:star::star:
{% endhint %}

In case of a NVIDIA driver update and after reboot, you only see a black screen, follow this guide to how downgrade the NVIDIA driver.

1. Open a Terminal
2. Go to `/var/cache/pacman/pkg` by typing the following command:

```powershell
PS> Set-Location /var/cache/pacman/pkg
```

3.  Now, lookup the correct package to downgrade, there are 3 to view:

    * nvidia-dkms
    * nvidia-utils
    * nvidia-settings

    You can search the version to downgrade by going on the following websites:

{% embed url="https://gitlab.archlinux.org/archlinux/packaging/packages/nvidia-utils/-/commits/main" %}
GitLab website for the NVIDIA Utils package
{% endembed %}

4. Now that you located the version, type the following command:

```powershell
PS> sudo pacman -U nvidia-dkms.123-4 nvidia-utils.123-4 nvidia-settings.123-4
```

5. Reboot the system when finished.

Congratulation you downgraded the NVIDIA Drivers!
