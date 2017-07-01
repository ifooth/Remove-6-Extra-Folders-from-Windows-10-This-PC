Remove 6 Extra Folders from Windows 10 Explorer “This PC”
=============================================================

When Windows 8.1 operating system was released, Microsoft renamed the good ol' Windows Explorer or My Computer to "This PC". Also to enhance "This PC" functionality and UI, Microsoft added 6 extra folder to it which were Desktop, Documents, Downloads, Music, Pictures and Videos.

For many people those extra folders were quite useless and were taking a good amount of space in "This PC" window. That's why we posted an exclusive tutorial to remove or hide those extra 6 folders from "This PC" window as well as tweaking and customizing other things. You can take a look at the tutorial at following link:

[Tips] Tweak and Customize Windows 8.1 Explorer "This PC"

Now Windows 10 has been released and it also comes with the same "This PC" window and 6 annoying folders. Unfortunately the old trick to get rid of these 6 folders which we shared for Windows 8.1, doesn't work in Windows 10.

![img](https://github.com/ifooth/Remove-6-Extra-Folders-from-Windows-10-This-PC/images/Extra_Folders_Windows_10_This_PC.png)

Its happening because Microsoft has changed the Registry keys and CLSIDs in Windows 10, that's why the old Registry script to remove those 6 folders is not applicable to Windows 10.

I investigated and looked into Windows 10 Registry Editor and finally found a way to remove those 6 folders. Though it took a bit time in finding those Registry keys.

Now in Windows 10, Microsoft is using a new string "ThisPCPolicy" in Registry to show or hide items in "This PC" window. If the string value is set to "Show", that particular item is shown in "This PC" window and if the string value is set to "Hide", that item is not shown in "This PC" window.

So we just need to change the value of "ThisPCPolicy" to "Hide" for all 6 folders CLSID in Registry and they will immediately disappear from "This PC" window.

If you also want to remove those extra and annoying 6 folders from Windows 10 "This PC" window, check out following simple steps:

1. Press WIN+R keys together to open RUN dialog box. You can also open it from WIN+X menu. Now type regedit in RUN dialog box and press Enter. It'll open Registry Editor.

2. Now go to following keys one by one:
```
For Pictures folder:
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\ FolderDescriptions\{0ddd015d-b06c-45d5-8c4c-f59713854639}\PropertyBag

For Videos folder:
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\ FolderDescriptions\{35286a68-3c57-41a1-bbb1-0eae73d76c95}\PropertyBag

For Downloads folder:
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\ FolderDescriptions\{7d83ee9b-2244-4e70-b1f5-5393042af1e4}\PropertyBag

For Music folder:
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\ FolderDescriptions\{a0c69a99-21c8-4671-8703-7934162fcf1d}\PropertyBag

For Desktop folder:
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\ FolderDescriptions\{B4BFCC3A-DB2C-424C-B029-7FE99A87C641}\PropertyBag

For Documents folder:
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\ FolderDescriptions\{f42ee2d3-909f-4907-8871-4c22fc0bf756}\PropertyBag
```
and change value of "ThisPCPolicy" string to Hide in each key.

![img](https://github.com/ifooth/Remove-6-Extra-Folders-from-Windows-10-This-PC/images/Hide_This_PC_Folders_Windows_10_Registry.png)

NOTE: All above mentioned keys contain "ThisPCPolicy" string except "{B4BFCC3A-DB2C-424C-B029-7FE99A87C641}" key which is responsible for Desktop folder. So you'll need to manually create new string "ThisPCPolicy" and set its value to Hide for this key.

3. That's it. Now open "This PC" window and you'll no longer see those extra 6 folders.

![img](https://github.com/ifooth/Remove-6-Extra-Folders-from-Windows-10-This-PC/images/No_Extra_Folders_Windows_10_This_PC.png)

UPDATE: Some 3rd party 32-bit programs may still show these unnecessary 6 folders in "Browse" dialog box such as Save, Save as or Open file as shown in following screenshot:

![img](https://github.com/ifooth/Remove-6-Extra-Folders-from-Windows-10-This-PC/images/Extra_Folders_Windows_10_Browse_Dialog_Box.png)

To remove these 6 folders from Browse window as well, you'll also need to set "ThisPCPolicy" string to Hide for following keys:
```
For Pictures folder in Browse window:
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\ Explorer\FolderDescriptions\{0ddd015d-b06c-45d5-8c4c-f59713854639}\PropertyBag

For Videos folder in Browse window:
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\ Explorer\FolderDescriptions\{35286a68-3c57-41a1-bbb1-0eae73d76c95}\PropertyBag

For Downloads folder in Browse window:
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\ Explorer\FolderDescriptions\{7d83ee9b-2244-4e70-b1f5-5393042af1e4}\PropertyBag

For Music folder in Browse window:
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\ Explorer\FolderDescriptions\{a0c69a99-21c8-4671-8703-7934162fcf1d}\PropertyBag

For Desktop folder in Browse window:
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\ Explorer\FolderDescriptions\{B4BFCC3A-DB2C-424C-B029-7FE99A87C641}\PropertyBag

For Documents folder in Browse window:
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\ Explorer\FolderDescriptions\{f42ee2d3-909f-4907-8871-4c22fc0bf756}\PropertyBag
```
PS: There is another easier way to change value of "ThisPCPolicy" string to Hide for all keys. Open Registry Editor, press Ctrl+F keys together to launch Find dialog box. Now type ThisPCPolicy and press Enter key. It'll go to the first key which contains this string. Now just change value of "ThisPCPolicy" string to Hide and then press F3 key to go to the next key containing the string. Again change value of the string to Hide for that key and press F3 key. Repeat these steps until you get "Finished searching through the registry" message. That's it, you are done.

NOTE: If you don't want to manually change keys and values in Registry, you can download following ready-made registry script to do the task automatically. Just download ZIP file, extract it using 7-Zip or any other file archive software and you'll get 2 .REG files to hide or show these 6 folders in Windows 10 "This PC" window:

Download Registry Script to Remove 6 Extra Folders from Windows 10 This PC

BONUS TIP:

If you noticed in the second screenshot, a DWORD "NoCustomize" is set to 1 for Desktop folder. This DWORD shows or hides "Customize This Folder" option in context menu of that particular folder. In other words, when you right-click in empty area of Desktop folder, you'll not get "Customize This Folder" option as its set to hidden using "NoCustomize" DWORD in Registry. You can set its value to 0 and the option "Customize This Folder" will be enabled in Desktop folder context menu. You can use this tip to show or hide the option for other folders as well.
