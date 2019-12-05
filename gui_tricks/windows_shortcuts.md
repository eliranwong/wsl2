# Windows startmenu shortcuts

At the time of writing, Windows startmenu shortcuts generated with pengwin-setup are not working for WSL2.

Below are the fixes.

# Create shortcuts with pengwin-setup

In the following examples, we use two GUI apps as examples:

To follow our examples, you may install the apps first.

> sudo apt install firefox-esr gnome-terminal

<b>AFTER</b> installing gui apps, run:

> pengwin-setup

Select "GUI > STARTMENU"

# Fixing shortcuts files

Download the following TWO files and put in ~/bin

https://github.com/eliranwong/wsl2/blob/master/bin/startmenu<br>
AND<br>
https://github.com/eliranwong/wsl2/blob/master/bin/startmenu2

[You may edit the file above to enable ibus as default input method.]

and run:

> chmod +x ~/bin/startmenu<br>
> chmod +x ~/bin/startmenu2

<b>Most GUI apps work with startmenu, while a few only work with startmenu2.</b>  Read the following description and examples for more details.

# Modify WSL Shortcuts Files

<b>Most GUI apps work with startmenu, while a few only work with startmenu2.</b>

We advise always try startmenu first.  If a particular GUI app does not work with startmenu, then use startmenu2.  In our testing, all GUI apps we tried work with at least one of the scripts.

To modify a WSL shortcut file:

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

4) <b>Apply the changes & double-click the file if the targeted GUI app is launched.</b>

5) <b>If it is not launched, repeat the steps above and use "startmenu2" instead of "startmenu".</b>

[If you are not sure what to search for and replace, option 2 below may be easier.]

<b>OPTION 2 - replace the whole line of shortcut target:</b>

1) Right-click a WSL shortcut file, generated with pengwin-setup.

2) Select "Properties"

3) Replace the whole line of "Target" field:

> pengwin run "cd~; ~/bin/startmenu [put your command here]"

4) Change "Run" option to "Minimized"

5) <b>Apply the changes & double-click the file if the targeted GUI app is launched.</b>

6) <b>If it is not launched, repeat the steps above and use "startmenu2" instead of "startmenu".</b>

# Two Examples:

We will use option 2 in the following examples.

One example uses "startmenu" another uses "startmenu2".

# Take "firefox" as an example

On start menu, right-click "FireFox ESR (WSL)" under Pengwin Applications.

Select more > "Open file location"

Right-click the Windows shortcut file "Firefox ESR (WSL)" and select "Properties".

Change <b>Target</b> to:

> pengwin run "cd~; ~/bin/startmenu firefox"

Change <b>Run</b> to:

> Minimized

Apply the changes.

Double-click the Windows shortcut file "Firefox (WSL)" to launch firefox.

# Take "gnome-terminal" as an example

[One of the reasons to use "gnome-terminal" instead of pengwin terminal is that pengwin terminal failed to display unicode characters when there is a mix of several different languages.]

Our "startmenu" script does not work with "gnome-terminal".  So, in the following example, we use "startmenu2" script instead.

On start menu, right-click "Terminal (WSL)" under Pengwin Applications.

Select more > "Open file location"

Right-click the Windows shortcut file "Terminal (WSL)" and select "Properties".

Change Target to:

> pengwin run "cd~; ~/bin/startmenu2 gnome-terminal --working-directory=\~"

Change Run to:

> Minimized

Apply the changes.

Double-click the Windows shortcut file "Terminal (WSL)" to launch gnome-terminal with fixed gui environment.

Please <b><a href="https://github.com/eliranwong/wsl2/blob/master/gui_tricks/terminal.md#remarks">the remarks HERE</a></b> for launching gnome-terminal via a Windows shortcut file.

# Create a Windows shortcut without pengwin-setup

1) Right-click an empty area within a folder in file explorer or desktop

2) New > Shortcut

3) Type the location of the item, for example. 

> pengwin.exe run "cd~; ~/bin/startmenu firefox"

4) Give a name

5) Right-click, select "Properties"

6) Remove the string in "Run in"

7) Run "Minimised"
