# gnome-terminal

Official pengwin terminal window does not support display unicdoe well.  Even you can change the font for display, it fails to display multiple non-English languages at the same time.  Gnome-terminal is a good alternative to it.

# To install

> sudo apt install gnome-terminal

# To run

> gnome-terminal

# To include .profile as a source

Edit > Preferences > Profiles > Command > Run command as a login shell

# To start with a directory
gnome-terminal --working-directory

# Copy & Paste

To copy:<br>
shift + ctrl + c<br>
[or select "Copy" from context menu, triggered by right-click]

To paste:<br>
shift + ctrl + v<br>
[or select "Paste" from context menu, triggered by right-click]

# To customise

Menubar > Edit > Profile Preferences

# To work with Thunar's "Custom Actions"

* Edit the pre-configured Custom Action - "Open Terminal Here"

In Thunar, select "Edit > Custom Actions > Open Terminal Here > Edit the currently selected action."

Enter in command:

> gnome-terminal --working-directory %f

* Add a Custom Action - "Open Terminal in Parent Directory"

In Thunar, select "Edit > Custom Actions > Add a new custome action."

Enter in command:

> gnome-terminal --working-directory %d

Use Startup Notification & Add Icon

In section, "Appearance Conditions":

File Pattern: *

Appears if selection contains: Audio Files, Image Files, Text Files, Video Files, Other Files
