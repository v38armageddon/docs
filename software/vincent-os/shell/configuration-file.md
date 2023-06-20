# Configuration file

By default, Vincent OS Shell create a .VOSshell.conf file when you start for the first time the shell. This file is located into your user folder.

* For Windows: C:\Users\\\<username>
* For Linux distros: /home/\<username>

This is a default configuration file content:

```editorconfig
# This is the default config file for Vincent OS Shell
# You can change the config file by using the command "conf"
# It open the config file in your default text editor
SHOW_TIME = False
SIMPLY_PATH = True
```

<table><thead><tr><th width="179">Syntax</th><th width="423">Definition</th><th>Default value</th></tr></thead><tbody><tr><td>SHOW_TIME</td><td>Show the current date and time at the start of the shell.</td><td>False</td></tr><tr><td>SIMPLY_PATH</td><td>Rather showing "&#x3C;Computer>\&#x3C;username>\&#x3C;path of the current directory>\vincentOS", it simplify the path by retiring only the "&#x3C;path of the current directory".</td><td>True</td></tr></tbody></table>
