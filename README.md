# wsl2
Notes on setup of Windows Subsystem for Linux (version 2)

Notes in this repository mainly describe the setup of pengwin version 1.3.4 in WSL2

# Use Latest Network Drivers

In our testings, micrsoft "Windows Update" app does not detect newer version of wifi driver on one of our devices.  The old driver did cause an issue under WSL2 [e.g. <a href="https://github.com/microsoft/WSL/issues/4253">a link here</a>, <a href="https://github.com/WhitewaterFoundry/Pengwin/issues/561">another link here</a>].

If you use Intel hardware, to make sure you get the latest drivers, go to the following link and install "Intel Driver & Support Assistant":

https://www.intel.com/content/www/us/en/support/intel-driver-support-assistant.html

Do a scan with the assistant and install the latest network drivers if newer versions are found.

# Notes on enabling WSL

https://docs.microsoft.com/en-us/windows/wsl/install-win10

# Notes on conversion between WSL1 & WSL2

https://www.pengwin.dev/blog/2019/6/12/enable-wsl2-and-convert-existing-pengwin-installations

# Setup X410 (PAID)

DPI Scaling > High Quality (Windowed Apps Only)

Shared Clipboard > Enable

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

# Setup Input Method

"fcitx", bundled with pengwin, is not working in WSL2 at the time of writing.

We recommend "ibus" instead.  For setup of ibus, read:

https://github.com/eliranwong/wsl2/blob/master/input_method/ibus.md

# Setup Terminal Apps

For issues with official pengwin terminal window and alternatives, you may read:

https://github.com/eliranwong/wsl2/blob/master/terminal/Readme.md

# Tricks for Launching GUI Apps

There were mutliple issues about running GUI apps with pengwin version earlier than 1.3.4 under WSL2.  Most know issues had been fixed with pengwin version 1.3.4.

Two suggestions here:

1) Add the following line to "~/.profile", if you need to work with .Xresources, e.g. https://github.com/eliranwong/wsl2/blob/master/terminal/urxvt.md#to-customise:

> xrdb -merge ~/.Xresources

2) To assign QStandardPaths for running Qt applications, app the following lines to file "~/.profile":

> mkdir -p /tmp/runtime-$USER<br>
> chmod 7700 /tmp/runtime-$USER<br>
> export XDG_RUNTIME_DIR=/tmp/runtime-$USER

# Fixing Windows Startmenu Shortcuts

For issues before pengwin version 1.3.4, you may read https://github.com/WhitewaterFoundry/Pengwin/issues/551.  Issues mentioned in the post had been fixed in pengwin version 1.3.4.

After installing multiple gui apps, run:

> pengwin-setup

select GUI > STARTMENU

The problem with creating shortcuts with pengwin-setup is that existing shortcuts are created again each time you run pengwin-setup > GUI > STARTMENU.  For examples, after installing 10 gui apps and run pengwin-setup > GUI > STARTMENU.  When you install one more gui app, running pengwin-setup > GUI > STARTMENU is ineffective because it creates shortcuts for all 11 gui apps.

A workaround is to use /usr/local/pengwin-setup.d/generate-shortcut.sh directly.  For example: https://github.com/eliranwong/wsl2/blob/master/bible_apps/desktop.md#create-a-windows-shortcut-recommended-for-pengwin-version-134

Alternatively, you can create a Windows shrotcut directly with Windows GUI.  For example: https://github.com/eliranwong/wsl2/blob/master/bible_apps/desktop.md#create-a-windows-shortcut-directly-on-windows

# WSL Utilities 

<a href='https://github.com/wslutilities/wslu'>WSL Utilities</a> are bundled with pengwin.  Read more about these utilities at https://github.com/wslutilities/wslu.

For example, to open a website, say https://github.com, using Windows default web browser, run

> wslview https://github.com

* <b>To WSL2 Users</b>, wslusc, bundled with pengwin version 1.3.4 does not work with WSL2.

Use /usr/local/pengwin-setup.d/generate-shortcut.sh instead.  For example: https://github.com/eliranwong/wsl2/blob/master/bible_apps/desktop.md#create-a-windows-shortcut-recommended-for-pengwin-version-134

Alternatively, you can create a Windows shrotcut directly with Windows GUI.  For example: https://github.com/eliranwong/wsl2/blob/master/bible_apps/desktop.md#create-a-windows-shortcut-directly-on-windows

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

To build font information cache files:

> fc-cache -f -v

To check all available fonts:

> fc-list

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

# Terminate a Distro

To check the name and version of a distro

> wsl.exe -l -v

To terminate a distro, e.g.

> wsl.exe -t WLinux

> wsl.exe -t Debian

> wsl.exe -t Ubuntu

# Shutdown Everything

Immediately terminates all running distributions and the WSL 2 lightweight utility virtual machine.

> wsl.exe --shutdown

# Restart WSL Service

Run from Windows PowerShell (Admin):

> Get-Service LxssManager | Restart-Service
