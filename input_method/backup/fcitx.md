# Backup: Notes for setting up fcitx on ChromeOS Crostini

ibus works better than fcitx on WSL2, please read the following article on setting up ibus for WSL2:

https://github.com/eliranwong/wsl2/blob/master/input_method/ibus.md

# Locale [optional / essential]

It is optional, becuase users don't need Chinese locale pack(s) for display of Chinese characters.<br>
HOWEVER, it is essential if you want to type Chinese on a Linux terminal, which we are going to desribe below [https://github.com/eliranwong/Chrome-OS-Linux/blob/master/non-english/chinese.md#use-fcitx-to-type-chinese-on-terminal].

An example:

* run in terminal: sudo nano /etc/locale.gen
* remove the comment sign before "zh_CN.UTF8 UTF8"
* to download language package(s), run in terminal: sudo locale-gen

# Set Default Locale [optional]

This changes default application menu & interface to Chinese.  It is optional.

1) To configure default language, run in terminal: sudo dpkg-reconfigure locales
2) select "zh_CN.UTF8 UTF8" as default locale

* Add variable for running applications launched through entering cmmands in terminal:

Use text editor to edit file ~/.bashrc, for example:

nano ~/.bashrc

Add the following lines at the end of the file:

export LC_ALL="zh_CN.UTF-8"<br>

In nano, Ctrl+O to save, Ctrl+X to exit.

Close and re-open terminal to make changes effective.

* Add variable for running applications launched through Chrome OS launcher menu:

Use text editor to edit file /etc/systemd/user/cros-garcon.service.d/cros-garcon-override.conf, for example:

sudo nano /etc/systemd/user/cros-garcon.service.d/cros-garcon-override.conf

Add the following lines at the end of the file:

Environment="LC_ALL=zh_CN.UTF-8"<br>

In nano, Ctrl+O to save, Ctrl+X to exit.

Close and re-open terminal to make changes effective.

[<b>Remarks:</b> This file might be overwritten in future updates.]

# Fonts

* Install available Chinese font packages [essential]:<br>
sudo apt install xfonts-wqy ttf-wqy-zenhei ttf-wqy-microhei fonts-arphic-bkai00mp fonts-arphic-bsmi00lp fonts-arphic-gbsn00lp fonts-arphic-gkai00mp xfonts-intl-chinese xfonts-intl-chinese-big

* Install user fonts [optional]:<br>
[It is optional, but you may consider it for WPS office to display characters properly.]<br>
For example, put all fonts in a folder "MyFonts" in "Downloads", then enter in terminal:<br>
mkdir ~/.fonts<br>
cp -r /mnt/chromeos/MyFiles/Downloads/MyFonts/ ~/.fonts/<br>
fc-cache -f -v<br>

* Check all installed font list<br>
fc-list<br>

* Check installed Chinese font list<br>
fc-list :lang=zh | cut -d: -f2<br>
fc-list :lang=zh | cut -d: -f1<br>
fc-list -f '%{family}\n' :lang=zh<br>

# Input Method - fcitx

<img src="example_wps.png">

The following example uses "fcitx".<br>
[To use "ibus" instead of "fcitx", read https://wiki.archlinux.org/index.php/IBus ]

1. Install fcitx:<br>
sudo apt install fcitx fcitx-frontend* fcitx-lib* libfcitx* fcitx-googlepinyin fcitx-table-cangjie5 opencc<br>
[optional: sudo apt install fcitx5*]

[Optional: To avoid potential conficts or free around 80MB of storage, enter in terminal:<br>
sudo apt remove fcitx-module-kimpanel]

2. Config fcitx as default input:<br>
sudo apt install im-config<br>
im-config<br>

* select "OK"
* select "Yes" to question "Do you explicitly select the user configuration?"
* select "fcitx"
* select "OK"
* select "OK"

<img src="fcitx.png"><br>

3. Add Variables

* For running applications launched through entering cmmands in terminal:

Use text editor to edit file ~/.bashrc, for example:

nano ~/.bashrc

Add the following lines at the end of the file:

export LC_CTYPE="zh_CN.UTF-8"<br>
export XIM="fcitx"<br>
export XIM_PROGRAM="/usr/bin/fcitx"<br>
export GTK_IM_MODULE="fcitx"<br>
export QT_IM_MODULE="fcitx"<br>
export XMODIFIERS="@im=fcitx"<br>

In nano, Ctrl+O to save, Ctrl+X to exit.

Close and re-open terminal to make changes effective.

* For running applications launched through Chrome OS launcher menu:

Use text editor to edit file /etc/systemd/user/cros-garcon.service.d/cros-garcon-override.conf, for example:

sudo nano /etc/systemd/user/cros-garcon.service.d/cros-garcon-override.conf

Add the following lines at the end of the file:

Environment="LC_CTYPE=zh_CN.UTF-8"<br>
Environment="XIM=fcitx"<br>
Environment="XIM_PROGRAM=/usr/bin/fcitx"<br>
Environment="GTK_IM_MODULE=fcitx"<br>
Environment="QT_IM_MODULE=fcitx"<br>
Environment="XMODIFIERS=@im=fcitx"<br>

In nano, Ctrl+O to save, Ctrl+X to exit.

Close and re-open terminal to make changes effective.

[<b>Remarks:</b> This file might be overwritten in future updates.]

4. Setup autostart of "fcitx" service

echo "/usr/bin/fcitx-autostart > /dev/null 2>&1" >> ~/.sommelierrc

Restart Linux to make changes effective.<br>

[Description on /dev/null: https://medium.com/@codenameyau/step-by-step-breakdown-of-dev-null-a0f516f53158]<br>
[Description on 2>&1: https://www.brianstorti.com/understanding-shell-script-idiom-redirect/]<br>

5. Setup keyboards

Enter in terminal:

fcitx-config-gtk3

* add "Google Pinyin" for typing simplified Chinese directly
* add "Cangjie5" for typing traditional Chinese directly
* to install only one Chinese keyboard for typing both traditional & simplified Chinese, you may consider conversion features which we will describe in the following sections.

<img src="keyboards.png"><br>

# Tips on Using "fcitx"

If you put "/usr/bin/fcitx-autostart > /dev/null 2>&1" in "~/.bashrc" or "~/.profile":<br>
* In order for Linux apps to work properly with "fcitx", open a Linux terminal window before target gui apps.<br>
* In our testing, terminal needs to be kept opened for "fcitx" to work properly in applications we tested.

<b>Solution:</b>

Put the command for auto-start of fcitx service in <b>~/.sommelierrc</b> instead:

echo "/usr/bin/fcitx-autostart > /dev/null 2>&1" >> ~/.sommelierrc

# Remarks on Running "fcitx" in Crostini

In our testings, "fcitx" works with the following applications:<br>
LibreOffice, WPS office, Dolphin, Thunar, Atom, Geany, Leafpad, etc.

However, not all Linux applications work with "fcitx" in Crostini.

Running "im-config", the message there tells us that it supports gtk2, gtk3 & qt4 frontends.  It does not mention qt5.  Even we installed fcitx-frontend-qt5, we haven't managed to run "fcitx" in our Qt5-based applications.  We also tried to manually copy /usr/lib/x86_64-linux-gnu/qt5/plugins/platforminputcontexts/libfcitxplatforminputcontextplugin.so to /Qt/plugins/platforminputcontexts/ folder of Qt5-based applications, but it does not work.

# Use Qt Virtual Keyboards for Qt5 applications

We mentioned above that some, if not all, Qt5 applications do not work with "fcitx".  We found a workaround is to use Qt virtual keyboards for typing Chinese in Qt5 applications.  To test if your Qt5 applications support Qt virtual keyboard, run the following in terminal before opening your applications:

export QT_IM_MODULE="qtvirtualkeyboard"

Our desktop bible application, UniqueBible.app, supports Qt virtual keyboards.  For more information, read https://github.com/eliranwong/Chrome-OS-Linux/blob/master/unique-bible-app/desktop.md#use-virtual-keyboard

# Typing Chinese on Terminal Emulator

You can type Chinese on Linux terminal emulator built-in with Chrome os.  Input methods assigned in Chrome os settings apply to the built-in Linux terminal emulator.  However, hitting "Ctrl + Space" on built-in terminal emulator does not change input method.  You need to manually change input method from "Keyboard" options, indicated in the following screenshot.

<img src="options.png"><br>

However, you may find display of Chinese characters is not smooth as expected.

<img src="built-in-terminal.png">

Keep reading if you want a solution.

# Use "fcitx" to type Chinese on Terminal

First, install "mlterm":<br>
sudo apt install mlterm

You can run "mlterm" in terminal or select the app icon from launcher menu as shown below:

<img src="mlterm.jpg">

A picture worth a thousand word, see below:

<img src="mlterm_typing.png">

Alternatively, consider <b>rxvt-unicode</b> for better copy-and-paste support:

https://github.com/eliranwong/Chrome-OS-Linux/blob/master/gui-apps-linux/Readme.md#terminal-emulator

# Conversion between Traditional & Simplified Chinese

* To install opencc:<br>
sudo apt install opencc<br>

* To configure opencc:<br>
Enter in Linux terminal: fcitx-config-gtk3<br>
Go to "Addon > Simplified Chinese To Traditional Chinese Convert ..."<br>
Select "OpenCC" and confirm "OK"<br>

* Enable / Disable conversion in apps, like libreoffice:<br>
Ctrl+Shift+f

<img src="conversion.png">

* Run opencc in terminal

Simplified Chinese to Traditional Chinese:<br>
opencc -i inputfile.txt -o outputfile.txt -c s2t.json

Traditional Chinese to Simplified Chinese<br>
opencc -i inputfile.txt -o outputfile.txt -c t2s.json

[More at: https://github.com/BYVoid/OpenCC]

* Custom actions in Thunar File Manager

Traditional Chinese to Simplified Chinese<br>
opencc -i %f -o %f_sc.txt -c t2s.json

Simplified Chinese to Traditional Chinese:<br>
opencc -i %f -o %f_tc.txt -c s2t.json

<img src="thunar.png">

# Pinyin Package

https://pypi.org/project/pypinyin/

To use pypinyin as a direct command in terminal, make sure path is updated:

echo "export PATH=$PATH:$HOME/.local/bin/" >> .bashrc

# Related Reference

https://wiki.debian.org/gnome-chinese-input

https://wiki.debian.org/InputMethodBuster

