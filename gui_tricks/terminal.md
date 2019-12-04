# Launch GUI apps via terminal

At the time of writing, running GUI apps via pengwin terminal in WSL2 is very broken.  Below are fixes.

# OPTION 1

save the following file in ~/bin

https://github.com/eliranwong/wsl2/blob/master/bin/gui

> chmod +x ~/bin/gui

> gui

When "Enter your command:" is prompted, simply enter a command to launch your GUI apps.  For example, type "firefox" and press ENTER.

# OPTION 2

save the following file in ~/bin

https://github.com/eliranwong/wsl2/blob/master/bin/guie

> chmod +x ~/bin/guie

> echo "source guie" >> ~/.bashrc

restart the terminal to make changes effective.

# OPTION 3

Alternatively, launch gnome-terminal via Windows startup shortcut

If you use our trick to launch "gnome-terminal" via Windows startmenu shortcut, you can skip the steps above and directly launch gui apps via gnome-terminal.

Read https://github.com/eliranwong/wsl2/blob/master/gui_tricks/windows_shortcuts.md#take-gnome-terminal-as-an-example
