# Thunar

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

<img src="thunar_open_explorer_2.png" />

[Appearance Conditions]<br>

File Patther:<br>
> *<br>

Appears if selection contains:<br>
> Directories<br>

# Other custom actions
