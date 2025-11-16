# Before Troubleshooting
When you encounter issues with Vincent OS, we recommend to check if there is a already a solution available in our different resources:
- [Forum](https://forum.v38armageddon.net/c/vincent-os/5)
- [r/VincentOS](https://www.reddit.com/r/VincentOS/?f=flair_name%3A%22Support%22)
- [r/v38armageddon](https://www.reddit.com/r/v38armageddon/?f=flair_name%3A%22Support%22)

Searching also for keywords related on your issue might help you find a solution faster.

```admonish tip
Vincent OS is based on Arch Linux, so most solutions for Arch Linux will also work for Vincent OS.
```

When asking for help, you can generate all your issue by including a log file. To do so, run the following command in a terminal:

```powershell
Start-Transcript -Path your_log_file.log
```

Then, reproduce the issue you are facing. Once done, stop the logging by running:

```powershell
Stop-Transcript
```

This will create a log file that you can share when asking for help.