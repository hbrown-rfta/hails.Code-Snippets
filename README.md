# hails.Code-Snippets

Various things.

## cmd_aliases.doskey

A set of doskey macros that map common Linux commands to their CMD equivalents, so you don't have to remember the Windows names. Each line is a macro in the form `name=definition`, where `$*` passes through any arguments you type.

| Alias | Maps to | Notes |
|-------|---------|-------|
| `clear` | `cls` | |
| `ls`, `ll` | `dir` | |
| `cat` | `type` | |
| `cp` | `copy` | |
| `mv` | `move` | |
| `rm` | `del` | Files only. Use `rmdir` for directories. |
| `grep` | `findstr` | |
| `which` | `where` | |
| `man` | `help` | |
| `pwd` | `cd` | |
| `ps` | `tasklist` | |
| `kill` | `taskkill` | |
| `ifconfig` | `ipconfig` | |
| `env` | `set` | |
| `history` | `doskey /history` | |
| `touch` | `type nul >` | Single filename only. |

### Registering cmd_aliases.doskey

To load the aliases automatically in every CMD window, register the file via the Command Processor AutoRun key:

```cmd
reg add "HKCU\Software\Microsoft\Command Processor" /v AutoRun /d "doskey /macrofile=\"C:\Users\hbrown\OneDrive - rfta.com\Documents\Scripts\CMD\cmd_aliases.doskey\"" /t REG_SZ /f
```

A few details that matter:

- The inner path is wrapped in escaped quotes (`\"`) because it contains spaces. Without them, CMD would cut the path off at the first space.
- `/f` forces the overwrite, so re-running the command updates the value instead of prompting.
- This sets AutoRun for the current user only (`HKCU`). Use `HKLM` instead if you want it for all users on the machine.
- After registering, open a fresh CMD window for the macros to take effect. They won't load in windows that were already open.

### Removing it later

To unregister, run:

```cmd
reg delete "HKCU\Software\Microsoft\Command Processor" /v AutoRun /f
```
