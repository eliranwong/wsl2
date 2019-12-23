# Install

sudo apt update<br>
sudo apt install apt-transport-https<br>
sudo sh -c 'curl https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -'<br>
sudo sh -c 'curl https://storage.googleapis.com/download.dartlang.org/linux/debian/dart_stable.list > /etc/apt/sources.list.d/dart_stable.list'<br>

sudo apt update<br>
sudo apt install dart<br>

# Add Path

Add the following line to ~/.profile

> export PATH=$PATH:/usr/lib/dart/bin:$HOME/.pub-cache/bin

# Install stegehand

pub global activate stagehand

# Install a Template

mkdir cli<br>
cd cli<br>
stagehand console-full

pub get

dart bin/main.dart

# Reference

https://dart.dev/tutorials/server/get-started
