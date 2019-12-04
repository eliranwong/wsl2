
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

> dbus-launch ibus-daemon -x -d

# To setup

> dbus-launch ibus-setup

<b>ATTENTION!</b> A restart of ibus service is necessary to make changes in setup effective.

# To restart ibus service

> pkill ibus-daemon<br>
> dbus-launch ibus-daemon -x -d

# To automate the service

> nano ~/.profile

dbus-launch ibus-daemon -x -d<br>
export LC_CTYPE="zh_CN.UTF-8"<br>
export XIM=ibus<br>
export XIM_PROGRAM=/usr/bin/ibus<br>
export QT_IM_MODULE=ibus<br>
export GTK_IM_MODULE=ibus<br>
export XMODIFIERS=@im=ibus<br>
export DefaultIMModule=ibus<br>

# Remove Potential Conflict with Fcitx

If you have fcitx installed via pengwing-setup, edit /etc/profile.d/fcitx.sh to remove fcitx-autostart and fcitx's variables.

Alternatively,

sudo rm /etc/profile.d/fcitx*
