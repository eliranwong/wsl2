# Thunar

Thunar is a file manager for Linux and other Unix-like systems

# Install

> sudo apt install thunar thunar-archive-plugin thunar-media-tags-plugin

# Open a Folder with "Windows Explorer"

# by Right-clicking a Folder

1) Go to "Edit > Configure custom actions..."
2) Add a new custom action.
3) Enter the following settings:

[Basic]<br>

Name & Description:<br>
> Open Windows Explorer Here<br>

Command:<br>
> explorer.exe $(echo %f | awk -F '/' '{print $NF}')<br>

<img src="thunar_open_explorer_1.png" />

[Appearance Conditions]<br>

File Patther:<br>
> *<br>

Appears if selection contains:<br>
> Directories<br>

<img src="thunar_open_explorer_2.png" />

# by Right-clicking a File

1) Go to "Edit > Configure custom actions..."
2) Add a new custom action.
3) Enter the following settings:

[Basic]<br>

Name & Description:<br>
> Open Windows Explorer in Parent Directory<br>

Command:<br>
> explorer.exe .<br>

[Appearance Conditions]<br>

File Patther:<br>
> *<br>

Appears if selection contains:<br>
> Text Files, Audio Files, Video Files, Image Files, Other Files<br>

# Launch gnome-terminal via thunar

https://github.com/eliranwong/wsl2/blob/master/terminal/gnome-terminal.md#to-work-with-thunars-custom-actions

# Launch Thunar from Windows Context Menu

1) Press Windows key + R and run "regedit" to open Registry Editor.

2) Go to "Computer\HKEY_CLASSES_ROOT\Directory\Background\shell\"

* Right-click "shell" and select "New > Key"
* Name the newly created key as "Thunar"
* Set the value of "(Default)" as "Open with Thunar"
* <b>INSIDE</b> Thunar, right-click and select "New > String Value"
* Name the newly created string as "Icon" and set the value as "C:\Users\elira\wslu\Thunar.ico"
* Right-click "Thunar" and select "New > Key"
* Name the newly created key as "command"
* Set the value of "(Default)" as:<br>
> C:\\Windows\\System32\\wscript.exe C:\\\\Users\\\\elira\\wslu\\runHidden.vbs "C:\\\\Users\\\\elira\\\\AppData\\\\Local\\\\Microsoft\\\\WindowsApps\\\\WhitewaterFoundryLtd.Co.16571368D6CFF_kd1vv0z0vy70w\\\\pengwin.exe" run "cd $(echo '\\"%V\\"' | sed -E -e 's/([A-Z]):\\\\/mnt\\/\\L\\1\\//' -e 's/\\\\/\\//g');  bash -l -c thunar"

Remarks: 
* The line above have been modified for rendering escape character \ on github page.  If you are reading this text in raw format, all double \ should be single when you enter the command in registry editor.
* Replace "elira" in the above command with your username.
* The most important part of the command is <b>run "cd $(echo '\\"%V\\"' | sed -E -e 's/([A-Z]):\\\\/mnt\\/\\L\\1\\//' -e 's/\\\\/\\//g');  bash -l -c thunar"</b>. You can copy the long string before the word "run" from a startmenu shortcut created by pengwin-setup. You can check the string by right-clicking a shortcut file and select "Properties".

3) Go to "Computer\HKEY_CLASSES_ROOT\Directory\shell"

* Right-click "shell" and select "New > Key"
* Name the newly created key as "Thunar"
* Set the value of "(Default)" as "Open with Thunar"
* <b>INSIDE</b> Thunar, right-click and select "New > String Value"
* Name the newly created string as "Icon" and set the value as "C:\Users\elira\wslu\Thunar.ico"
* Right-click "Thunar" and select "New > Key"
* Name the newly created key as "command"
* Set the value of "(Default)" as:<br>
> C:\\Windows\\System32\\wscript.exe C:\\\\Users\\\\elira\\wslu\\runHidden.vbs "C:\\\\Users\\\\elira\\\\AppData\\\\Local\\\\Microsoft\\\\WindowsApps\\\\WhitewaterFoundryLtd.Co.16571368D6CFF_kd1vv0z0vy70w\\\\pengwin.exe" run "cd $(echo '\\"%V\\"' | sed -E -e 's/([A-Z]):\\\\/mnt\\/\\L\\1\\//' -e 's/\\\\/\\//g');  bash -l -c thunar"

Remarks: 
* The line above have been modified for rendering escape character \ on github page.  If you are reading this text in raw format, all double \ should be single when you enter the command in registry editor.
* Replace "elira" in the above command with your username.
* The most important part of the command is <b>run "cd $(echo '\\"%V\\"' | sed -E -e 's/([A-Z]):\\\\/mnt\\/\\L\\1\\//' -e 's/\\\\/\\//g');  bash -l -c thunar"</b>. You can copy the long string before the word "run" from a startmenu shortcut created by pengwin-setup. You can check the string by right-clicking a shortcut file and select "Properties".

<img src="registry_editor_1.png" />

<img src="registry_editor_2.png" />

<img src="add_thunar_to_context_menu.png" />
