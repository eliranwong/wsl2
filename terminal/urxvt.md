# rxvt-unicode

# To install

> sudo apt install rxvt-unicode

# To run:<br>
> urxvt

# To customise

1) Open ~/.Xresources:<br>
> nano ~/.Xresources

2) add the following lines to the file:<br>
URxvt.background: #000000<br>
URxvt.foreground: #FFFFFF<br>
URxvt.color4: #1E90FF<br>
URxvt.color12: #0081FF<br>
URxvt.font: xft:NSimSun:pixelsize=18<br>
URxvt.perl-ext-common: selection-to-clipboard<br>
URxvt.letterSpace: 0

3) Run in terminal:<br>
> xrdb -merge ~/.Xresources

# Copy & Paste

To copy and paste within urxvt itself:<br>
Paste content from other gui applications:<br>
alt+Ctrl+v

# To work with our GUI scripts

In our scripts available at:

https://github.com/eliranwong/wsl2/tree/master/bin

change this line:

> #xrdb -merge ~/.Xresources

to:

> xrdb -merge ~/.Xresources
