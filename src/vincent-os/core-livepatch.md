# Core LivePatch
```admonish warning
Not to be confused with Kernel Livepatching and kpatch, (see: [https://wiki.archlinux.org/title/Kernel\_live\_patching](https://wiki.archlinux.org/title/Kernel_live_patching), [https://www.redhat.com/fr/blog/introducing-kpatch-dynamic-kernel-patching](https://www.redhat.com/fr/blog/introducing-kpatch-dynamic-kernel-patching))
```

## Definition
Core LivePatch (abbreviated to CLP) allows you to update critical Vincent OS part via patches without rebooting your computer.

```admonish note
An automated systemd service runs on the background to manage the update and apply all patches. It runs all days at 12H00 (24h format).

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

----
## Developer Informations
Source code of Core LivePatch can be found in the [Vincent OS GitHub repository](https://github.com/Vincent-OS/clpctl).

Core LivePatch is made in C# and use the latest .NET LTS version. It is dependent on the following packages:
- `dotnet-runtime-X.Y` (where X.Y is the latest .NET LTS version, e.g., 8.0)
- `powershell-bin` (see Scripts part)

### Structure of a .clp file
A `.clp` file is a zip compressed archive. Minimum required files:
```
CLPRYYMMDD.clp
├── PKGINFO.meta        # XML metadata (name, description, etc.)
├── Install-Script.ps1  # PowerShell script executed to apply the patch
└── Remove-Script.ps1   # PowerShell script executed to rollback the patch
```

### Scripts
#### Install-Script.ps1
This PowerShell script is executed when applying the patch. It should contain all necessary commands to update the system.

Example:
```powershell
#!/usr/bin/pwsh
# Patch Creator: Your Name
# Date: XXXX-XX-XX

$patchFiles=(
	# Define your files here
	"tmp/example-patch/new-file.txt",
	"tmp/example-patch/modified-file.txt",
	"tmp/example-patch/removed-file.txt"
)
$ogPatchDir="/opt/CLP/$(Split-Path -Leaf (Get-Location))"
$backupDir="${ogPatchDir}/backup"

Start-Transcript -Path "/var/log/CLP.log" -Append

# Because we are never sure if the system is stable, we create a backup
# of the files we are going to modify.
function Confirm-BackupDirectory {
	mkdir $backupDir
	Write-Host "[INFO] Backup directory created at $backupDir"
}

function Backup-File {
	param (
		[string]$file
	)

	if (Test-Path -Path $file) {
		Copy-Item -Path $file -Destination $backupDir
		Write-Host "[INFO] Successfully backed up: $file"
	}
	else {
		Write-Warning "[WARNING] File: $file not found. Skipping backup."
	}
}

function Restore-Action {
	$revertScript = Join-Path -Path (Get-Location) -ChildPath "Remove-Patch.ps1"
	if (Test-Path -Path $revertScript) {
		Write-Host "[INFO] Reverting changes..."
		& $revertScript
	}
	else {
		Write-Error "[ERROR] Remove-Patch.ps1 is missing or not executable. Aborting."
		exit 2
	}
}

function Install-Patch {
	Confirm-BackupDirectory
	foreach ($file in $patchFiles) {
		Backup-File -File $file
		switch ($file) {
			"tmp/example-patch/new-file.txt" {
				Write-Host "[INFO] Installing new file: $file"
				Copy-Item -Path $file -Destination "/opt/CLP/new-file.txt"
			}
			"tmp/example-patch/modified-file.txt" {
				Write-Host "[INFO] Modifying file: $file"
				Copy-Item -Path $file -Destination "/opt/CLP/modified-file.txt" -Force
			}
			"tmp/example-patch/removed-file.txt" {
				Write-Host "[INFO] Removing file: $file"
				Remove-Item -Path "/opt/CLP/removed-file.txt" -Force
			}
			default {
				Write-Error "[FATAL] An unknown error occurred while applying the patch."
				Write-Error "[FATAL] Reverting all changes."
				./Remove-Patch.ps1
			}
		}
	}
	Write-Host "[INFO] All files installed successfully. Processed files:"
	foreach ($file in $patchFiles) {
		Write-Host "  - $file"
	}
	Stop-Transcript
	exit 0
}

Install-Patch
```
#### Remove-Script.ps1
This PowerShell script is executed when rolling back the patch. It should contain all necessary commands to revert the changes made by the `Install-Script.ps1`.

Example:
```powershell
#!/usr/bin/pwsh
# Patch Creator: Your Name
# Date: XXXX-XX-XX

$patchFiles=@(
	# Define your files here
	"tmp/example-patch/new-file.txt"
	"tmp/example-patch/modified-file.txt"
	"tmp/example-patch/removed-file.txt"
)
$ogPatchDir="/opt/CLP/$(Split-Path -Leaf (Get-Location))"
$backupDir="${ogPatchDir}/backup"

Start-Transcript -Path "/var/log/CLP.log" -Append

foreach ($file in $patchFiles) {
	$backupFile = Join-Path -Path $backupDir -ChildPath (Split-Path -Leaf $file)
	if (Test-Path $backupFile) {
		Write-Host "[INFO] Restoring file: $backupFile"
		Copy-Item -Path -Verbose $backupFile -Destination $file
	}
	else {
		Write-Warning "[WARNING] Backup file not found: $backupFile"
	}
}
Write-Host "[INFO] All files restored successfully."

Stop-Transcript
```