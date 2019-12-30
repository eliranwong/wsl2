# Setup Microsoft Visual Studio Code

Do NOT install Visual Studio Code with pengwin-setup.

Install the Windows version.<br>
<b>AND</b><br>
Install extension "Remote - WSL"

With this setup, you can use Visual Studio Code from both Windows and WSL.

To launch Visual Studio Code from a Linux terminal, run:

> code

or

> code [filename]

or

> code .

More at:<br>
* https://code.visualstudio.com/docs/remote/wsl
* https://code.visualstudio.com/remote-tutorials/wsl/run-in-wsl

Optional Settings:

Telemetry: Enable Telemetry > False

Telemetry: Enable Crash Reporter > False

Files: Eol > \n

Terminal > External: Linux Exec > gnome-terminal

# Configure Custome Action in Thunar File Manager

Name & Description:<br>
> Open with Code

Command:<br>
> code %f

Apperance Conditions:<br>
> Directories, Text Files

Read more about configuring Thunar at: https://github.com/eliranwong/wsl2/blob/master/file_manager/thunar.md
