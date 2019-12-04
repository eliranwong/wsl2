# Windows startmenu shortcuts

At the time of writing, Windows startmenu shortcuts generated with pengwin-setup are not working.  Below are the fixes.

# Take Windows shortcut for "gnome-terminal" as an example

[Though we use "gnome-terminal" shortcut as an example, it applies to other shortcuts.]

Download the following file and put in ~/bin

https://github.com/eliranwong/wsl2/blob/master/bin/startmenu

and run:

> chmod +x ~/bin/startmenu



On start menu, right-click Terminal (WSL) under Pengwin Applications.

Select more > "Open file location"

Right-click the Windows shortcut file "Terminal (WSL)" and select "properties".

Change Target to:

> pengwin run "cd~; ~/bin/startmenu 'gnome-terminal --working-directory=\~'"

Change Run to:

> Minimized

Apply the changes.

Double-click the Windows shortcut file "Terminal (WSL)" to launch gnome-terminal with fixed gui environment.
