# Before Troubleshooting
When you encounter issues with WebSM, we recommend to check if there is a already a solution available in our different resources:
- [Forum](https://forum.v38armageddon.net/c/software/websm/10)
- [r/v38armageddon](https://www.reddit.com/r/v38armageddon/?f=flair_name%3A%22WebSM%22)

Searching also for keywords related on your issue might help you find a solution faster.

When asking for help, you can generate a log file. To do so, run the following command in a terminal:

```powershell
Start-Transcript -Path your_log_file.log
```

Then, reproduce the issue you are facing by launching WebSM from the terminal. Once done, stop the logging by running:

```powershell
Stop-Transcript
```

This will create a log file that you can share when asking for help.