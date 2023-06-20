# execute

{% hint style="warning" %}
You need to type `execute`, then the type of the script, then the file.

This problem will be resolved in a future update.
{% endhint %}

This command allows you to execute a PowerShell script or a CMD script. It allows the following type of files.

| PowerShell | CMD  |
| ---------- | ---- |
| .ps1       | .bat |
| .psm1      | .cmd |
| .psd1      | .btm |
|            | .vbs |

Examples:

```bash
COMPUTER\Username\vincentOS:\> execute
>> ps_script
>> Example.ps1
```

```bash
COMPUTER\Username\vincentOS:\> execute
>> cmd_script
>> Example.bat
```
