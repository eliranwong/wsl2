
# ibus

"fcitx" is very broken in some applications, running under pengwin.  "iBus" works much better under pengwin.

# Preparation

You do not need to change your default language, but you need to install the package of your target language.  The example below install a Chinese package, WITHOUT changing default language to Chinese.

* run in terminal: sudo nano /etc/locale.gen
* remove the comment sign before "zh_CN.UTF8 UTF8"
* to download language package(s), run in terminal: sudo locale-gen

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

# To automate the service [recommended from pengwin version 1.3.4 onwards]

Create file /etc/profile.d/ibus.sh, with the following content:

> export LC_CTYPE="zh_CN.UTF-8"
> export XIM=ibus
> export XIM_PROGRAM=/usr/bin/ibus
> export QT_IM_MODULE=ibus
> export GTK_IM_MODULE=ibus
> export XMODIFIERS=@im=ibus
> export DefaultIMModule=ibus
> ibus-daemon -drx

# Remove Potential Conflict with Fcitx [recommended]

If you have fcitx installed via pengwing-setup, edit /etc/profile.d/fcitx.sh to remove fcitx-autostart and fcitx's variables.

Alternatively,

sudo rm /etc/profile.d/fcitx*

# Using ibus with a touch-screen

We found ibus works perfectly with Windows virtual keyboard.

Press Ctrl + space on Windows virtual keyboard can switch ibus input methods.

