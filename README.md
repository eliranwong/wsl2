# wsl2
Notes on setup of Windows Subsystem for Linux (version 2)

Notes in this repository mainly describe the setup of pengwin & x410 in WSL2

# Notes on conversion between WSL1 & WSL2

https://www.pengwin.dev/blog/2019/6/12/enable-wsl2-and-convert-existing-pengwin-installations

# Setup X410 (PAID)

DPI Scaling > High Quality (Windowed Apps Only)

Shared Clipboard > Enable

Shared Clipboard > Auto copy to Windows after selection

Miscellaneous Options > Capture Windows Key

To work with WSL2, select "Allow Public Access"

Remarks: Set Windows firewall according to your needs.

# VCXSRV (FREE)

You may consider VCXSRV as an alternative to X410.  In our testing, windowed apps work better in X410 due to its feature "DPI Scaling > High Qaulity".  You don't need to install VCXSRV if you have X410 installed.

It is not recommended to install VCXSRV via pengwin-setup.

Instead, we recommend to install VCXSRV via Windows PowerShell (Admin):
[Reason: It is easier to use XLaunch from start menu for configuration.]

> choco install vcxsrv

To make "vcxsrv" to work with google web engine or QtWebEngine, select from XLaunch "Native OpenGL".

To make "vcxsrv" to work with WSL2, select from XLaunch "Disable Access Control".

# Update Installed Packages

> sudo apt update<br>
> sudo apt dist-upgrade

# Setup Common Tools

> sudo apt install apt-utils build-essential cmake tree wget curl git zip unzip xz-utils nano lib32stdc++6 sqlite3 libsqlite3-dev libnss3 libncurses5 libncurses5-dev libgl1-mesa-dev mesa-utils binutils dbus-x11 opencc

# Setup with pengwin-setup

<b>RECOMMENDED:</b>

GUI > FCITX [installed for testing, it is currently not working in WSL2]

GUI > GUILIB

PROGRAMMING > PYTHONPI

SETTINGS > EXPLORER

SETTINGS > COLORTOOL

<b>NOT RECOMMENDED:</b>

"GUI > HIDPI"

# Edit /etc/profile.d/00-pengwin.sh

<b>CHANGE</b> from:

> export DISPLAY=:0

to:

> export DISPLAY=$(cat /etc/resolv.conf | grep nameserver | awk '{print $2}'):0.0

<b>CHANGE</b> from:

> export LIBGL_ALWAYS_INDIRECT=1

to:

> unset LIBGL_ALWAYS_INDIRECT

# Remove /etc/profile.d/dbus.sh

This file currently breaks input method and some other GUI apps.

> sudo rm /etc/profile.d/dbus.sh

We fix the dbus_session issues with our tricks at:

https://github.com/eliranwong/wsl2/blob/master/gui_tricks/terminal.md

# Setup Input Method

"fcitx", bundled with pengwin, is not working in WSL2 at the time of writing.

We recommend "ibus" instead.  For setup of ibus, read:

https://github.com/eliranwong/wsl2/blob/master/input_method/ibus.md

# Setup Terminal Apps

pengwin terminal is not good for displaying different languages at the same time.  For example, pengwin terminal window failed to compare English, Chinese, Hebrew & Greek bible verses at the same time.

We recommend "rxvt-unicode" and "gnome-terminal", read this link for setup:

https://github.com/eliranwong/wsl2/tree/master/terminal

# Tricks for Launching GUI Apps

Read https://github.com/eliranwong/wsl2/blob/master/gui_tricks/terminal.md

# Fixing Windows Startmenu Shortcuts

Read https://github.com/eliranwong/wsl2/blob/master/gui_tricks/windows_shortcuts.md

# Setup Bible Apps

Command line version of UniqueBible.app:

https://github.com/eliranwong/wsl2/blob/master/bible_apps/command_line.md

Desktop version of UniqueBible.app:

https://github.com/eliranwong/wsl2/blob/master/bible_apps/desktop.md

# Setup Other GUI Apps

sudo apt install geany geany-plugins rxvt-unicode gnome-terminal thunar sqlitebrowser falkon gthumb gedit gnome-keyring

[Remarks: gnome-keyring is required for running mailspring.]

* Office<br>
wps office [https://www.wps.com/download] shows better compatibilities with ms files than libreoffice.

* mail client<br>
mailspring is available for download at https://getmailspring.com/. Mailspring works with gmail signin whereas thunderbird doesn't.
