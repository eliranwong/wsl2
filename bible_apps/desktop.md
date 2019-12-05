# Desktop version repository

https://github.com/eliranwong/UniqueBible

# Installation in WSL2 (Windows Subsystem for Linux Version 2)

In our testing, UniqueBible requires version 2 of WSL to work.  It does not run with version 1 of WSL.

In the following example, we install desktop version of UniqueBible.app in pengwin with WSL2.

# Installation

Install "PYTHONPI" via pengwin-setup > PROGRAMMING

Alternatively, run in terminal

> sudo apt install python3 python3-setuptools python3-pip python3-venv

Download UniqueBible

> cd ~

> git clone https://github.com/eliranwong/UniqueBible

Setup virtual environment & depedencies

> cd ~/UniqueBible

> python3 -m venv venv

> pip3 install PySide2 PyPDF2 gdown python-docx

# Create a Shortcut

For example:

Download the following file and save to your home directory:

https://github.com/eliranwong/UniqueBible/blob/master/shortcut_uba_Windows_wsl2.sh
[Remarks: Edit ubaFolder="$HOME/UniqueBible/" on line 3 if you do not place UniqueBible folder in home directory.]

Add permission:

> chmod +x ~/shortcut_uba_Windows_wsl2.sh

Add alias:

> echo "alias uba=~/shortcut_uba_Windows_wsl2.sh" >> ~/.bashrc

# Run with alias:

> uba

# Create a Windows shortcut file [recommended]

Download "startmenu" script first, read:<br>
https://github.com/eliranwong/wsl2/blob/master/gui_tricks/windows_shortcuts.md#fixing-shortcuts-files

After creating a Windows shortcut file, you can launch the app by:<br>
- double-clicking a shortcut file<br>
- using keyboard shortcuts

<b>To create a Windows shortcut file for UniqueBible.app, for example:</b>

1) Right-click an empty area on desktop

2) New > Shortcut

3) Type the location of the item, for example. 

> pengwin run "cd ~/UniqueBible; source venv/bin/activate; ~/bin/startmenu python3 main.py"

4) Name your shortcut, e.g. "UniqueBible.app (WSL)", and select "Finish"

5) Right-click the created shortcut file, select "Properties"

6) Empty the string in "Start in"

7) In the field of "Shortcut key:", pressing "Ctrl + Alt + B" at the same time

8) Run "Minimized"

9) Download this icon https://github.com/eliranwong/UniqueBible/blob/master/htmlResources/theText.ico

10) Change icon

<img src="shortcut_properties.png" />

# Change default font

Some characters may not be displayed correctly or nicely with your Linux default font.

You can change the default font for displaying text in UniqueBible.app.

Change the 2nd line of ~/UniqueBible/htmlResources/theText.css, from

> /* font-family: 'Calibri'; */

to:

> font-family: 'Calibri';

If you prefer a font other than 'Calibri', simply replace it with your favourite font.

# Shared marvelData folder in Windows Drive C [optional]

You can install a copy in Windows drive C and a copy in WSL2.

Both copies can share a single marvelData folder without duplication of storage.

In our testing, we have a copy of marvelData in Windows drive C at:<br>
C:\Users\elira\OneDrive\Documents\UniqueBible\marvelData

In our testing, we edited the file config.py of our LINUX copy [NOT Window copy] on line 4:

marvelData = '/home/eliran/winhome/OneDrive/Documents/UniqueBible/marvelData'

Remarks: DO NOT edit file config.py while the app is running.

Remarks: While sharing a single folder in this example may offer convenience, be aware of the issue on slower cross os file speed in current preview build of wsl2, mentioned at https://docs.microsoft.com/en-us/windows/wsl/wsl2-ux-changes#cross-os-file-speed-will-be-slower-in-initial-preview-builds .  Until the issue is fixed by microsoft wsl team, we advise using UniqueBible.app with marvelData folder located under the same os.
