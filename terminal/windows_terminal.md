# Setup Windows Terminal (Preview)

Microsoft "Windows Terminal (Preview)" supports unicode characters.

# To install

It can be downloaded via "Microsoft Store" app or run in "Windows PowerShell (Admin)" if "Chocolately" is installed:

> choco install microsoft-windows-terminal

# To set a WSL terminal as default & change starting directory:

1) Open "Windows Terminal (Preview)"
2) Select "Settings"
3) To change the value of "defaultProfile" to the guid of your WSL distro profile
4) To change starting directory, e.g.

>    "defaultProfile": "{11111111-1111-1111-1111-111111111111}",

>...
>...

        {
            "guid": "{11111111-1111-1111-1111-111111111111}",
            "hidden": false,
            "name": "WLinux",
            "source": "Windows.Terminal.Wsl",
            "startingDirectory": "\\\\wsl$\\WLinux\\home\\eliranwong\\"
        },

# Keyboard Shortcuts

close a tab: Ctrl+Shift+w

open a new tab: Ctrl+Shift+t

duplicate a tab: Ctrl+Shift+d

copy: Ctrl+Shift+c

paste: Ctrl+Shift+v
