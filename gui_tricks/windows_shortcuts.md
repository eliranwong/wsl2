# Windows startmenu shortcuts

At the time of writing, Windows startmenu shortcuts generated with pengwin-setup are not working for WSL2.

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

# Modify WSL Shortcuts Files

On start menu, right-click a WSL shortcut file under Pengwin Applications.

Select more > "Open file location"

<b>OPTION 1 - search & replace of shrotcut target:</b>

1) Right-click a WSL shortcut file, generated with pengwin-setup.

2) Select "Properties"

3) Inside the long line of "Traget" field,

search for and replace:

> export DISPLAY=:0;

with:

> ~/bin/startmenu

[If you are not sure what to search for and replace, option 2 below is easier for most users.]

<b>OPTION 2 - replace the whole line of shortcut target:</b>

1) Right-click a WSL shortcut file, generated with pengwin-setup.

2) Select "Properties"

3) Replace the whole line of "Target" field:

> pengwin run "cd~; ~/bin/startmenu [put your command here]"

4) Change "Run" option to "Minimized"

We will use option 2 in the following examples.

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
