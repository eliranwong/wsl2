# gnome-terminal

Official pengwin terminal window does not support display unicdoe well.  Even you can change the font for display, it fails to display multiple non-English languages at the same time.  Gnome-terminal is a good alternative to it.

# To install

> sudo apt install gnome-terminal

# To run

> gnome-terminal

# To include .profile as a source

Edit > Preferences > Profiles > Command > Run command as a login shell

# To start with a directory
gnome-terminal --working-directory

# Copy & Paste

To copy:<br>
shift + ctrl + c<br>
[or select "Copy" from context menu, triggered by right-click]

To paste:<br>
shift + ctrl + v<br>
[or select "Paste" from context menu, triggered by right-click]

# To customise

Menubar > Edit > Profile Preferences

# To work with Thunar's "Custom Actions"

* Edit the pre-configured Custom Action - "Open Terminal Here"

In Thunar, select "Edit > Custom Actions > Open Terminal Here > Edit the currently selected action."

Enter in command:

> gnome-terminal --working-directory %f

* Add a Custom Action - "Open Terminal in Parent Directory"

In Thunar, select "Edit > Custom Actions > Add a new custome action."

Enter in command:

> gnome-terminal --working-directory %d

Use Startup Notification & Add Icon

In section, "Appearance Conditions":

File Pattern: *

Appears if selection contains: Audio Files, Image Files, Text Files, Video Files, Other Files

# Launch Gnome-Terminal from Windows Context Menu

1) Press Windows key + R and run "regedit" to open Registry Editor.

2) Go to "Computer\HKEY_CLASSES_ROOT\Directory\Background\shell\"

* Right-click "shell" and select "New > Key"
* Name the newly created key as "GnomeTerminal"
* Set the value of "(Default)" as "Open with Gnome Terminal"
* <b>INSIDE</b> GnomeTerminal, right-click and select "New > String Value"
* Name the newly created string as "Icon" and set the value as "C:\Users\elira\wslu\org.gnome.Terminal.ico"
* Right-click "GnomeTerminal" and select "New > Key"
* Name the newly created key as "command"
* Set the value of "(Default)" as:<br>
> C:\\Windows\\System32\\wscript.exe C:\\\\Users\\\\elira\\wslu\\runHidden.vbs "C:\\\\Users\\\\elira\\\\AppData\\\\Local\\\\Microsoft\\\\WindowsApps\\\\WhitewaterFoundryLtd.Co.16571368D6CFF_kd1vv0z0vy70w\\\\pengwin.exe" run "cd $(echo '\\"%V\\"' | sed -E -e 's/([A-Z]):\\\\/mnt\\/\\L\\1\\//' -e 's/\\\\/\\//g');  bash -l -c gnome-terminal"

Remarks: 
* The line above have been modified for rendering escape character \ on github page.  If you are reading this text in raw format, all double \ should be single when you enter the command in registry editor.
* Replace "elira" in the above command with your username.
* The most important part of the command is <b>run "cd $(echo '\\"%V\\"' | sed -E -e 's/([A-Z]):\\\\/mnt\\/\\L\\1\\//' -e 's/\\\\/\\//g');  bash -l -c gnome-terminal"</b>. You can copy the long string before the word "run" from a startmenu shortcut created by pengwin-setup. You can check the string by right-clicking a shortcut file and select "Properties".

3) Go to "Computer\HKEY_CLASSES_ROOT\Directory\shell"

* Right-click "shell" and select "New > Key"
* Name the newly created key as "GnomeTerminal"
* Set the value of "(Default)" as "Open with Gnome Terminal"
* <b>INSIDE</b> GnomeTerminal, right-click and select "New > String Value"
* Name the newly created string as "Icon" and set the value as "C:\Users\elira\wslu\org.gnome.Terminal.ico"
* Right-click "GnomeTerminal" and select "New > Key"
* Name the newly created key as "command"
* Set the value of "(Default)" as:<br>
> C:\\Windows\\System32\\wscript.exe C:\\\\Users\\\\elira\\wslu\\runHidden.vbs "C:\\\\Users\\\\elira\\\\AppData\\\\Local\\\\Microsoft\\\\WindowsApps\\\\WhitewaterFoundryLtd.Co.16571368D6CFF_kd1vv0z0vy70w\\\\pengwin.exe" run "cd $(echo '\\"%V\\"' | sed -E -e 's/([A-Z]):\\\\/mnt\\/\\L\\1\\//' -e 's/\\\\/\\//g');  bash -l -c gnome-terminal"

Remarks: 
* The line above have been modified for rendering escape character \ on github page.  If you are reading this text in raw format, all double \ should be single when you enter the command in registry editor.
* Replace "elira" in the above command with your username.
* The most important part of the command is <b>run "cd $(echo '\\"%V\\"' | sed -E -e 's/([A-Z]):\\\\/mnt\\/\\L\\1\\//' -e 's/\\\\/\\//g');  bash -l -c gnome-terminal"</b>. You can copy the long string before the word "run" from a startmenu shortcut created by pengwin-setup. You can check the string by right-clicking a shortcut file and select "Properties".
