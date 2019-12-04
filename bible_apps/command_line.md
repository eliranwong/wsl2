# Command Line Version

Repository at: https://github.com/eliranwong/bible

# Install dart SDK

It looks like dart SDK works in WSL2 but not in WSL1.  In WSL1, running "pub get" command receives errors "connection closed while receiving data".  "pub get" runs smoothly in WSL2.

https://github.com/eliranwong/Chrome-OS-Linux/blob/master/development-tools/dart_sdk.md

# Install "bible" project in Linux

There are several ways to get the project run on Linux device, below is an example.

> cd ~<br>
> git clone https://github.com/eliranwong/bible<br>
> cd bible<br>
> stagehand console-full --override<br>
> pub get<br>
> mv bin/main.dart_copy bin/main.dart<br>

# Add alias

> echo 'alias bible="cd $HOME/bible; dart bin/main.dart"' >> ~/.bashrc

close and re-open the terminal to make changes effective

# Run

To read quick notes on supported commands, enter in terminal:
bible

To open a passage, enter in terminal, e.g.:
bible open John 3

# Customisation

Add more bibles:<br>
add bibles to folder "assets/bible"

Convert Bibles from UniqueBible.app desktop version:<br>
Install desktop version: https://github.com/eliranwong/Chrome-OS-Linux/blob/master/unique-bible-app/desktop.md<br>
Install the bibles you want<br>
Convert bibles with ThirdParty.py<br>
e.g. enter in terminal:<br>
python3<br>
from ThirdParty import Converter<br>
Converter().exportJsonBible("KJV")

Change path of resource folder:<br>
edit "~/bible/lib/config.dart"<br>
for example, to put all resources in USB:<br>
var resourceFolder = "/mnt/chromeos/removable/EliranUSB/Linux/bible/assets";<br>
[For accessing USB from Crostini, read https://github.com/eliranwong/Chrome-OS-Linux#access-usb-drive-from-linux-apps]


# Standalone app

Two advantages:
1) standalone app runs faster
2) standalone app can run without dart sdk

cd ~/bible<br>
dart2native bin/main.dart -o bin/bible

Change alias in ~/.bashrc:<br>
alias bible="$HOME/bible/bin/bible"

If you do not need dart SDK anymore, you can remove it to free around 500MB of disk space:<br>
sudo apt remove dart
