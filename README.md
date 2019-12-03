# wsl2
Notes on setup of Windows Subsystem for Linux (version 2)

Notes in this repository mainly describe the setup of pengwin & x410 in WSL2

# Notes on conversion between WSL1 & WSL2

https://www.pengwin.dev/blog/2019/6/12/enable-wsl2-and-convert-existing-pengwin-installations

# Update Installed Packages

> sudo apt update<br>
> sudo apt dist-upgrade

# Setup with pengwin-setup

# Setup Common Tools

> sudo apt install apt-utils build-essential cmake tree wget curl git zip unzip xz-utils nano lib32stdc++6 sqlite3 libsqlite3-dev libnss3 libncurses5 libncurses5-dev libgl1-mesa-dev mesa-utils binutils dbus-x11 opencc

# Setup Input Method

"fcitx", bundled with pengwin, is not working in WSL2 at the time of writing.

# Setup Terminal Apps

pengwin terminal is not good for displaying different languages at the same time.  For example, pengwin terminal window failed to compare English, Chinese, Hebrew & Greek bible verses at the same time.

We recommend "rxvt-unicode" and "gnome-terminal".

We recommend "ibus" instead.

# Setup GUI Apps

# Setup Bible Apps
