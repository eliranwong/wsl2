# Windows startmenu shortcuts

At the time of writing, Windows startmenu shortcuts generated with pengwin-setup are not working.

Below are the fixes.

# Create shortcuts with pengwin-setup

In the following examples, we use two GUI apps as examples:

To follow our examples, you may install the apps first.

> sudo apt install gedit gnome-terminal

<b>AFTER</b> installing your gui apps, run:

> pengwin-setup

Select "GUI > STARTMENU"

# Fixing shortcuts files

Download the following file and put in ~/bin

https://github.com/eliranwong/wsl2/blob/master/bin/startmenu

[You may edit the file above to enable ibus as default input method.]

and run:

> chmod +x ~/bin/startmenu

Read examples below to change shortcut's "Target" to:

> pengwin run "cd~; ~/bin/startmenu [put your command here]"

# Take "gnome-terminal" as an example

On start menu, right-click "Terminal (WSL)" under Pengwin Applications.

Select more > "Open file location"

Right-click the Windows shortcut file "Terminal (WSL)" and select "Properties".

Change Target to:

> pengwin run "cd~; ~/bin/startmenu gnome-terminal --working-directory=\~"

Change Run to:

> Minimized

Apply the changes.

Double-click the Windows shortcut file "Terminal (WSL)" to launch gnome-terminal with fixed gui environment.

# Take "gedit" as an example

On start menu, right-click "Text Editor (WSL)" under Pengwin Applications.

Select more > "Open file location"

Right-click the Windows shortcut file "Text Editor (WSL)" and select "Properties".

Change <b>Target</b> to:

> pengwin run "cd~; ~/bin/startmenu gedit"

Change <b>Run</b> to:

> Minimized

Apply the changes.

Double-click the Windows shortcut file "Text Editor (WSL)" to launch gedit.
