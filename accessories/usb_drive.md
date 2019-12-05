# Mount a USB drive in WSL1

To mount a usb drive, e.g. drive d:

> sudo mkdir /mnt/d<br>
> sudo mount -t drvfs d: /mnt/d

To unmount:

> sudo umount /mnt/d

Drives formatted as FAT, ExFAT or NTFS can be mounted in WSL.

# Workaround in WSL2

The mount method metioned above doesn't work in WSL2

Workaround is to run the following in a Linux folder:

> explorer.exe .

Please note that there is a dot "." at the end.

In this way, you can use Windows "File Explorer" to move files between USB drive and Linux folders.
