## Overview
This troubleshooting exercise documents the diagnosis and recovery of a corrupted Zsh command history file on Kali Linux.

## Environment
- **Operating System:** Kali Linux
- **Shell:** Zsh
- **Affected File:** `/home/kali/.zsh_history`

## Problem
Upon opening the terminal, Zsh displayed the following error:

```bash
zsh: corrupt history file /home/kali/.zsh_history
```

This indicated that the shell's command history file had become corrupted, potentially due to an interrupted write operation or improper shutdown.

## Troubleshooting & Resolution

### 1. Created a Backup
Before modifying the corrupted file, I created a backup to preserve the original data.

```bash
cp ~/.zsh_history ~/.zsh_history.backup
```

### 2. Recovered Readable History
Used the Linux `strings` utility to extract readable text from the corrupted history file and write it to a clean history file.

```bash
strings ~/.zsh_history.backup > ~/.zsh_history
```

### 3. Corrected File Permissions
Restored appropriate permissions to the history file.

```bash
chmod 600 ~/.zsh_history
```

### 4. Reloaded Zsh
Restarted the Zsh shell to load the repaired history file.

```bash
exec zsh
```

### 5. Verified Recovery
Executed the following command to verify that command history was accessible again.

```bash
history
```

## Outcome
Successfully recovered readable command history and restored normal Zsh history functionality.

## Skills Demonstrated
- Linux command-line troubleshooting
- Zsh shell administration
- File backup and recovery
- Linux file permissions
- Text processing with `strings`
- Problem diagnosis and verification

## Lessons Learned
This exercise reinforced the importance of backing up configuration files before modifying them and verifying system functionality after troubleshooting.

**Note:** The `strings` utility recovers readable text, not necessarily every original history entry. The original backup was retained to preserve the source data.
