---
title: "Delete Additional Keyboard on Windows10"
date: 2023-03-19T15:23:50+03:00
draft: false
tags: [dev, utility, windows, keyboard]
---

# Why the need?
## Why the Keyboard Layout
Anyone with a non-english country probably has one or more languages and probably their respective keyboard layouts available to them.  
In Turkey, we have a Turkish-Q keyboard layout and our keyboards are mostly in this layout as hardware.  
Here is a quick glance of how it is, thanks to Microsoft: https://learn.microsoft.com/en-us/globalization/keyboards/kbdtuq.html

## What has changed in Windows10
You used to delete this additional keyboard layout so that it just doesn't switch from one to the other during your usage.  
It seems there's a bug in Windows so you can't do what you've been able to do previously.  
Details of the bug is here: https://answers.microsoft.com/en-us/windows/forum/windows_10-other_settings/unable-to-remove-a-language-from-windows-10-april/47c13ea5-79ed-4a29-96d4-47d1264b6838

# Solution
Thankfully, the article also includes a workaround also:
```powershell
    #It's just powershell, execute following 4 lines
    #For me, the keyboard layout's language code was: "en-US", change if needed
    #To learn which languages exists as keyboard layout, just execute "Get-WinUserLanguageList"
    
    $LangList = Get-WinUserLanguageList
    $MarkedLang = $LangList | where LanguageTag -eq "en-US"
    $LangList.Remove($MarkedLang)
    Set-WinUserLanguageList $LangList -Force
```

That's it. Here it stays if I need that again.