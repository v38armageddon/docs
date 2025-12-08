# Updating with pacman failed due to keyring issues
```admonish info
Difficulty level: ⭐
```

When updating your system with pacman, if you encounter the following error related to keyring issues:

```
error: <repo>: signature from "<key>" is invalid
error: failed to synchronize all databases (unexpected error)
```

This indicates that the repository signature cannot be verified due to missing or untrusted keys in your keyring.
To resolve this issue, you can download the [CLP125112](https://repo.v38armageddon.net/vincent-os/CLP/CLP1251124.clp) and execute it:
```bash
clpctl install CLP1251124.clp
```
This will install the missing keys and allow you to update your system without further keyring issues.

## Manual method
If you prefer to manually update the keyring, you can follow these steps:
1. **Add the missing keys**: Identify the missing keys from the error message and add them to your keyring using the following command:
   ```bash
   pacman-key --recv-keys <key>
   ```
2. **Sign the keys**: After adding the keys, sign them to mark them as trusted:
   ```bash
   pacman-key --lsign-key <key>
   ```
3. **Update the keyring package**: Ensure that your keyring package is up to-date:
   ```bash
   pacman-key --refresh-keys
   ```

You should now be able to update your system without encountering keyring issues.