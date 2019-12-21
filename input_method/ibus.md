
# ibus

"fcitx" is very broken in some applications, running under pengwin.  "iBus" works much better under pengwin.

# To install

> sudo apt install ibus ibus-libpinyin ibus-table-cangjie5 ibus-gtk* ibus-qt*

# To set default input method

> im-config

select "OK"<br>
select "Yes" to question "Do you explicitly select the user configuration?"<br>
select "ibus"<br>
select "OK"<br>
select "OK"<br>

# To start ibus service

> dbus-launch ibus-daemon -drx

# To setup

> dbus-launch ibus-setup

<b>ATTENTION!</b> A restart of ibus service is necessary to make changes in setup effective.

# To restart ibus service

> pkill ibus-daemon<br>
> dbus-launch ibus-daemon -drx

# To automate the service [not recommended]

You can set variables and automate the service.

> nano ~/.profile

export LC_CTYPE="zh_CN.UTF-8"<br>
export XIM=ibus<br>
export XIM_PROGRAM=/usr/bin/ibus<br>
export QT_IM_MODULE=ibus<br>
export GTK_IM_MODULE=ibus<br>
export XMODIFIERS=@im=ibus<br>
export DefaultIMModule=ibus<br>
dbus-launch ibus-daemon -drx<br>

It is <b>NOT recommended</b> to automate the service the way above, because "dbus-launch ibus-daemon -drx" work for some apps only.

To make input method to work with all GUI apps, take a look at our tricks on running GUI apps.

https://github.com/eliranwong/wsl2/tree/master/gui_tricks

To launch GUI apps from terminal we recommend "gnome-terminal", read:<br>
https://github.com/eliranwong/wsl2/blob/master/gui_tricks/terminal.md#option-3---use-gnome-terminal<br>
and<br>
https://github.com/eliranwong/wsl2/blob/master/gui_tricks/windows_shortcuts.md#take-gnome-terminal-as-an-example

To launch GUI apps via Windows shortcut files, you may read our notes at:<br>
https://github.com/eliranwong/wsl2/blob/master/gui_tricks/windows_shortcuts.md

# Remove Potential Conflict with Fcitx [recommended]

If you have fcitx installed via pengwing-setup, edit /etc/profile.d/fcitx.sh to remove fcitx-autostart and fcitx's variables.

Alternatively,

sudo rm /etc/profile.d/fcitx*

# Using ibus with a touch-screen

We found ibus works perfectly with Windows virtual keyboard.

Press Ctrl + space on Windows virtual keyboard can switch ibus input methods.

