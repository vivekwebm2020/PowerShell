# PowerShell
PowerShell scripts for Mick's IT Blogs

### General Issues with reference links to answers / solutions:
Q1. "Run with Powershell" context menu item disappeared / removed accidentally.  
A1. Follow the correct answer given here: https://github.com/PowerShell/PowerShell/issues/14216#issue-748123628
Or just follow the code given here: https://github.com/PowerShell/PowerShell/issues/14216#issuecomment-1084010061  

Code below:
```reg
Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\SystemFileAssociations\.ps1]

[HKEY_CLASSES_ROOT\SystemFileAssociations\.ps1\Shell]

[HKEY_CLASSES_ROOT\SystemFileAssociations\.ps1\Shell\Edit]
"NoSmartScreen"=""

[HKEY_CLASSES_ROOT\SystemFileAssociations\.ps1\Shell\Edit\Command]
@="\"C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\powershell_ise.exe\" \"%1\""

[HKEY_CLASSES_ROOT\SystemFileAssociations\.ps1\Shell\RunPowershell5AsAdmin]
@="Run with Powershell 5 as Admin"

[HKEY_CLASSES_ROOT\SystemFileAssociations\.ps1\Shell\RunPowershell5AsAdmin\command]
@="\"C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\powershell.exe\" \"-Command\" \"\"& {Start-Process PowerShell.exe -ArgumentList '-ExecutionPolicy RemoteSigned -File \\\"%1\\\"' -Verb RunAs}\""

[HKEY_CLASSES_ROOT\SystemFileAssociations\.ps1\Shell\RunPowershell7]
@="Run with Powershell 7 - non admin"

[HKEY_CLASSES_ROOT\SystemFileAssociations\.ps1\Shell\RunPowershell7\Command]
@="C:\\Program Files\\PowerShell\\7\\pwsh.exe -Command \"$host.UI.RawUI.WindowTitle = 'PowerShell 7 (x64)'; if((Get-ExecutionPolicy ) -ne 'AllSigned') { Set-ExecutionPolicy -Scope Process Bypass }; & '%1'\""

[HKEY_CLASSES_ROOT\SystemFileAssociations\.ps1\Shell\RunPowershell7AsAdmin]
@="Run with Powershell 7 as Admin"

[HKEY_CLASSES_ROOT\SystemFileAssociations\.ps1\Shell\RunPowershell7AsAdmin\Command]
@="\"C:\\Program Files\\PowerShell\\7\\pwsh.exe\" \"-Command\" \"\"& {Start-Process pwsh.exe -ArgumentList '-ExecutionPolicy RemoteSigned -File \\\"%1\\\"' -Verb RunAs}\""

[HKEY_CLASSES_ROOT\SystemFileAssociations\.ps1\Shell\Windows.PowerShell.Run]
"MUIVerb"=hex(2):40,00,22,00,25,00,73,00,79,00,73,00,74,00,65,00,6d,00,72,00,\
  6f,00,6f,00,74,00,25,00,5c,00,73,00,79,00,73,00,74,00,65,00,6d,00,33,00,32,\
  00,5c,00,77,00,69,00,6e,00,64,00,6f,00,77,00,73,00,70,00,6f,00,77,00,65,00,\
  72,00,73,00,68,00,65,00,6c,00,6c,00,5c,00,76,00,31,00,2e,00,30,00,5c,00,70,\
  00,6f,00,77,00,65,00,72,00,73,00,68,00,65,00,6c,00,6c,00,2e,00,65,00,78,00,\
  65,00,20,00,22,00,2c,00,2d,00,31,00,30,00,38,00,00,00
@="Run with Powershell 5"

[HKEY_CLASSES_ROOT\SystemFileAssociations\.ps1\Shell\Windows.PowerShell.Run\Command]
@="\"C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\powershell.exe\" \"-Command\" \"if((Get-ExecutionPolicy ) -ne 'AllSigned') { Set-ExecutionPolicy -Scope Process Bypass }; & '%1'\""
```
Q2. How to set the folder for saving the Recorded videos in VLC Media Player ?  
A2. https://wiki.videolan.org/VLC_HowTo/Set_the_recording_folder/
 - Navigate to Tools -> Preferences -> Input&codecs and Record directory or filename.
 - Note: Press `Save` button to save VLC settings and _restart VLC after that_ to make sure changes are enabled.
