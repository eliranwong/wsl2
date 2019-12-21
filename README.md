# wsl2
Notes on setup of Windows Subsystem for Linux (version 2)

Notes in this repository mainly describe the setup of pengwin & x410 in WSL2

# Notes on enabling WSL

https://docs.microsoft.com/en-us/windows/wsl/install-win10

# Notes on conversion between WSL1 & WSL2

https://www.pengwin.dev/blog/2019/6/12/enable-wsl2-and-convert-existing-pengwin-installations

# Setup X410 (PAID)

DPI Scaling > High Quality (Windowed Apps Only)

Shared Clipboard > Enable

Shared Clipboard > Auto copy to Windows after selection

Miscellaneous Options > Capture Windows Key

To work with WSL2, select "Allow Public Access"

Remarks: Set Windows firewall according to your needs.

# Alternative to X410 - VCXSRV (FREE)

You may consider VCXSRV as an alternative to X410.

We do not recommended installing VCXSRV via pengwin-setup.

Instead, we recommend installing VCXSRV via Windows PowerShell (Admin):
[Reason: It is easier to use XLaunch from start menu for configuration.]

> choco install vcxsrv

To make "vcxsrv" to work with google web engine or QtWebEngine, select from XLaunch "Native OpenGL".

To make "vcxsrv" to work with WSL2, select from XLaunch "Disable Access Control".

<b>Comment:</b>

In our testing, windowed apps work better and look nicer in X410, as it offers a feature "DPI Scaling > High Qaulity".  You don't need to install VCXSRV if you have X410 installed.

# Autostart Display Server

It is better to start display server before launching a GUI app.  To start a display server automatically, for example, X410

Open Windows "Run" app, 

to open apps folder

> shell:appsfolder

to open startup folder

> shell:startup

To create link in startup, drag X410 from apps folder to startup folder

# Update Installed Packages

> sudo apt update<br>
> sudo apt dist-upgrade

# Setup Common Tools

> sudo apt install apt-utils build-essential cmake tree wget curl git zip unzip xz-utils nano lib32stdc++6 sqlite3 libsqlite3-dev libasound2 libnss3 libncurses5 libncurses5-dev libgl1-mesa-dev mesa-utils lsb-release binutils dbus-x11 youtube-dl ffmpeg gawk translate-shell opencc

# Examples on Command-line Tools

* Download Youtube Video / Audio

https://github.com/eliranwong/wsl2/blob/master/multimedia/youtube-dl.md

# Setup with pengwin-setup

<b>RECOMMENDED:</b>

GUI > GUILIB

GUI > SYNAPTIC

PROGRAMMING > GO

PROGRAMMING > PYTHONPI

SETTINGS > EXPLORER

SETTINGS > COLORTOOL

<b>NOT RECOMMENDED:</b>

GUI > FCITX [It breaks in many GUI apps under WSL2]

"GUI > HIDPI" [instead, use X410 > DPI Scaling > High Quality (Windowed Apps Only)]

# Edit /etc/profile.d/00-pengwin.sh

The following applies to pengwin version earlier than 1.3.4 only.

<b>CHANGE</b> from:

> export DISPLAY=:0

to:

> export DISPLAY=$(cat /etc/resolv.conf | grep nameserver | awk '{print $2}'):0.0

<b>CHANGE</b> from:

> export LIBGL_ALWAYS_INDIRECT=1

to:

> unset LIBGL_ALWAYS_INDIRECT

[Remarks: Make sure you have mesa-utils in place, read https://github.com/eliranwong/wsl2#setup-common-tools.  "unset LIBGL_ALWAYS_INDIRECT" is essential for running GUI apps using OpenGL.]

# Remove /etc/profile.d/dbus.sh

The following applies to pengwin version earlier than 1.3.4 only.

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

We recommend "rxvt-unicode" and "gnome-terminal" as alternatives, read this link for setup:

https://github.com/eliranwong/wsl2/tree/master/terminal

<b>Comment:</b>

"gnome-terminal" is easier to be configured.  Copy & Paste in "gnome-terminal" can be done through right-click context menu or keyboard shortcuts.  We like "Tab" features of "gnome-terminal" too.

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

To install available packages:

> sudo apt install gedit geany geany-plugins rxvt-unicode gnome-terminal thunar thunar-archive-plugin thunar-media-tags-plugin sqlitebrowser firefox-esr flashplugin-nonfree falkon gnome-keyring libsecret* libreoffice gthumb gimp

[Remarks: ibus works with all the above GUI apps tested in both WSL1 & WSL2 whereas fcitx works only in some applications in WSL1.  At the time of writing, fcitx is broken in WSL2.]<br>
[Remarks: Some of GUI apps above, e.g. falkon, work only in version 2 of WSL.]<br>
[Remarks: gnome-keyring & libsecret* are required for running mailspring.]

* Office<br>
wps office [https://www.wps.com/download] shows better compatibilities with ms files than libreoffice.

* mail client<br>
mailspring is available for download at https://getmailspring.com/. Mailspring works with gmail signin whereas thunderbird doesn't.
To verify gmail signin with mailspring, use Linux browser installed in WSL2 instead of using browser installed in Windows directory. Use Firefox / Chrome / Opera instead of falkon for gmail signin verification.

* Web browser<br>
In our testings, chrome and opera browsers work in WSL2, but not in WSL1<br>
Chrome is available at: https://www.google.com/chrome/<br>
Opera is available at: https://www.opera.com/<br>
Chrome works the best with signin of mutliple gmail accounts.

# Additions of Fonts

We find that we don't need to add any fonts on Linux side, as with pengwin, our tested GUI applications can use fonts installed on Windows side directly.

For examples, we have fonts "NSimSun" and "Calibri" instalaled on Windows on our device.

We assign Windows font "NSimSun" to a Linux terminal app:<br>
https://github.com/eliranwong/wsl2/blob/master/terminal/urxvt.md#to-customise

We assign Windows font "Calibri" to a Linux GUI app:<br>
https://github.com/eliranwong/wsl2/blob/master/bible_apps/desktop.md#change-default-font

# Setup mlocate

To install:<br>
> sudo apt install mlocate

To create database:<br>
> sudo /etc/cron.daily/mlocate

To manually update the database:<br>
> sudo updatedb

To run:

> locate

or

> mlocate

# GUI for pacakage management

> sudo synaptic

# Workaround to work with USB drive in WSL2

https://github.com/eliranwong/wsl2/blob/master/accessories/usb_drive.md

# Restart WSL Service

Run from Windows PowerShell (Admin):

> Get-Service LxssManager | Restart-Service
