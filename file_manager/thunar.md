# Thunar

Thunar is a file manager for Linux and other Unix-like systems

# Install

> sudo apt install thunar thunar-archive-plugin thunar-media-tags-plugin

# Open a Folder with "Windows Explorer"

1) Go to "Edit > Configure custom actions..."
2) Add a new custom action.
3) Enter the following settings:

[Basic]<br>

Name & Description:<br>
> Open Windows Explorer Here<br>

Command:<br>
> explorer.exe $(echo %f | awk -F '/' '{print $NF}')<br>

<img src="thunar_open_explorer_1.png" />

[Appearance Conditions]<br>

File Patther:<br>
> *<br>

Appears if selection contains:<br>
> Directories<br>

<img src="thunar_open_explorer_2.png" />

# Launch gnome-terminal via thunar

https://github.com/eliranwong/wsl2/blob/master/terminal/gnome-terminal.md#to-work-with-thunars-custom-actions
