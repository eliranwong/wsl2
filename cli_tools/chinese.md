# Locale [essential for Chinese input method]

An example:

* run in terminal: sudo nano /etc/locale.gen
* remove the comment sign before "zh_CN.UTF8 UTF8"
* to download language package(s), run in terminal: sudo locale-gen

Pengwin users can use pengwin-setup to install Chinese lauguage pack without seting it as the default locale.

# Set Default Locale [optional]

This changes default language of application menu & interface to Chinese.  It is <b>OPTIONAL</b>, you can use Chinese input method, without configuring Chinese as the default locale, provided that you have Chinese language pack installed.

1) To configure default language, run in terminal: sudo dpkg-reconfigure locales
2) select "zh_CN.UTF8 UTF8" as default locale

Pengwin users can use pengwin-setup to install a Chinese pack and set Chinese as default locale.

* Add variable to ~/.bashrc:

> echo "export LC_ALL=zh_CN.UTF-8" >> ~/.bashrc

# Fonts [optional]

It is optional becuase Linux GUI apps under pengwin's WSL can use fonts available on Windows.

* Install available Chinese font packages [essential]:<br>
sudo apt install xfonts-wqy ttf-wqy-zenhei ttf-wqy-microhei fonts-arphic-bkai00mp fonts-arphic-bsmi00lp fonts-arphic-gbsn00lp fonts-arphic-gkai00mp xfonts-intl-chinese xfonts-intl-chinese-big

* Check all installed font list<br>
fc-list<br>

* Check installed Chinese font list<br>
fc-list :lang=zh | cut -d: -f2<br>
fc-list :lang=zh | cut -d: -f1<br>
fc-list -f '%{family}\n' :lang=zh<br>

# Conversion between Traditional & Simplified Chinese

* To install opencc:<br>
> sudo apt install opencc<br>

* Enable / Disable conversion in apps:<br>
Ctrl+Shift+f

* Run opencc in terminal

Simplified Chinese to Traditional Chinese:<br>
> opencc -i inputfile.txt -o outputfile.txt -c s2t.json

Traditional Chinese to Simplified Chinese<br>
> opencc -i inputfile.txt -o outputfile.txt -c t2s.json

[More at: https://github.com/BYVoid/OpenCC]

* Custom actions in Thunar File Manager

Traditional Chinese to Simplified Chinese<br>
> opencc -i %f -o %f_sc.txt -c t2s.json

Simplified Chinese to Traditional Chinese:<br>
> opencc -i %f -o %f_tc.txt -c s2t.json

# Pinyin Package

https://pypi.org/project/pypinyin/

To use pypinyin as a direct command in terminal, make sure path is updated:

> echo "export PATH=$PATH:$HOME/.local/bin/" >> .bashrc

# Related Reference

https://wiki.debian.org/gnome-chinese-input

https://wiki.debian.org/InputMethodBuster
