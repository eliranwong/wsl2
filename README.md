# wsl2
Notes on setup of Windows Subsystem for Linux (version 2)

Notes in this repository mainly describe the setup of pengwin & x410 in WSL2

# Notes on conversion between WSL1 & WSL2

https://www.pengwin.dev/blog/2019/6/12/enable-wsl2-and-convert-existing-pengwin-installations

# Update Installed Packages

> sudo apt update<br>
> sudo apt dist-upgrade

# Setup Common Tools

> sudo apt install apt-utils build-essential cmake tree wget curl git zip unzip xz-utils nano lib32stdc++6 sqlite3 libsqlite3-dev libnss3 libncurses5 libncurses5-dev libgl1-mesa-dev mesa-utils binutils dbus-x11 opencc

# Setup with pengwin-setup

# Essential Changes

* Edit /etc/profile.d/00-pengwin.sh

<b>CHANGE</b> from:

> export DISPLAY=:0

to:

> export DISPLAY=$(cat /etc/resolv.conf | grep nameserver | awk '{print $2}'):0.0

<b>CHANGE</b> from:

> export LIBGL_ALWAYS_INDIRECT=1

to:

> unset LIBGL_ALWAYS_INDIRECT

* Edit /etc/profile.d/dbus.sh

<b>CHANGE</b> from:

> eval "DBUS_SESSION_BUS_ADDRESS='tcp:host=localhost,port=42701,guid=6bb5626ef77b33289609c0a75de4614b';<br>
> export DBUS_SESSION_BUS_ADDRESS;<br>
> DBUS_SESSION_BUS_PID=1513;"<br>

to:

> export $(dbus-launch --exit-with-x11 | grep DBUS_SESSION_BUS_ADDRESS);<br>
> export $(dbus-launch --exit-with-x11 | grep DBUS_SESSION_BUS_PID);

# Setup Input Method

"fcitx", bundled with pengwin, is not working in WSL2 at the time of writing.

# Setup Terminal Apps

pengwin terminal is not good for displaying different languages at the same time.  For example, pengwin terminal window failed to compare English, Chinese, Hebrew & Greek bible verses at the same time.

We recommend "rxvt-unicode" and "gnome-terminal".

We recommend "ibus" instead.

# Setup GUI Apps

# Setup Bible Apps
