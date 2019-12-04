# Windows startmenu shortcuts

At the time of writing, Windows startmenu shortcuts generated with pengwin-setup are not working.  Below are the fixes.

# Fixing shortcuts files

Download the following file and put in ~/bin

https://github.com/eliranwong/wsl2/blob/master/bin/startmenu

and run:

> chmod +x ~/bin/startmenu

Read examples below to change shortcut's "Target" to:

> pengwin run "cd~; ~/bin/startmenu '[put your command here]'"

# Take shortcut for "gnome-terminal" for an example

On start menu, right-click Terminal (WSL) under Pengwin Applications.

Select more > "Open file location"

Right-click the Windows shortcut file "Terminal (WSL)" and select "properties".

Change Target to:

> pengwin run "cd~; ~/bin/startmenu 'gnome-terminal --working-directory=\~'"

Change Run to:

> Minimized

Apply the changes.

Double-click the Windows shortcut file "Terminal (WSL)" to launch gnome-terminal with fixed gui environment.
