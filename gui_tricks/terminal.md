# Launch GUI apps via terminal

At the time of writing, running GUI apps via pengwin terminal in WSL2 is very broken.  Below are fixes.

# OPTION 1 - user interaction

save the following file in ~/bin

https://github.com/eliranwong/wsl2/blob/master/bin/gui

> chmod +x ~/bin/gui

> gui

When "Enter your command:" is prompted, simply enter a command to launch your GUI apps.  For example, type "firefox" and press ENTER.

# OPTION 2 - pre-loaded environment [recommended]

save the following file in ~/bin

https://github.com/eliranwong/wsl2/blob/master/bin/guie

> chmod +x ~/bin/guie

> echo "source $HOME/bin/guie" >> ~/.bashrc

restart the terminal to make changes effective.

# OPTION 3 - use "gnome-terminal"

Alternatively, launch gnome-terminal via Windows startmenu shortcut.
[The reason to use gnome-terminal is that pengwin terminal fails to display unicode characters when there is a mix of different languages.]

If you use our script to launch "gnome-terminal" via Windows startmenu shortcut, you can skip the option 1 above and directly launch any GUI apps via gnome-terminal.

Read https://github.com/eliranwong/wsl2/blob/master/gui_tricks/windows_shortcuts.md#take-gnome-terminal-as-an-example

# Remarks

If you use option 3, you have to implement option 2 as well.  It looks like a duplication, but it fixes the dbus_session issues and input method for all GUI apps launched from the gnome-terminal opened with a Windows startmenu shortcut.
