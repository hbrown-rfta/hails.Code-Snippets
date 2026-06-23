# hails.Code-Snippets
Various things.  


## Registering cmd_aliases.doskey  
To load the aliases automatically in every CMD window, register the file via the Command Processor AutoRun key:  
```CMD
reg add "HKCU\Software\Microsoft\Command Processor" /v AutoRun /d "doskey /macrofile=\"C:\Users\hbrown\OneDrive - rfta.com\Documents\Scripts\CMD\cmd_aliases.doskey\"" /t REG_SZ /f
```

#### A few details that matter:  
The inner path is wrapped in escaped quotes (\") because it contains spaces. Without them, CMD would cut the path off at the first space.  
/f forces the overwrite, so re-running the command updates the value instead of prompting.  

This sets AutoRun for the current user only (HKCU). Use HKLM instead if you want it for all users on the machine.  
After registering, open a fresh CMD window for the macros to take effect. They won't load in windows that were already open.  

##### To remove it later, run:  
```CMD
reg delete "HKCU\Software\Microsoft\Command Processor" /v AutoRun /f
```
