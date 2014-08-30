Ionic Cordova Android Docker Image
==================================
[![Stories in Ready](https://badge.waffle.io/nicopace/ionic-cordova-android-vagrant-docker.png?label=ready&title=Ready)](https://waffle.io/nicopace/ionic-cordova-android-vagrant-docker)

A Docker image complete with Ionic, Node, Cordova, and Android installed for quick development of apps.

To use it, you will require Docker in your system. To install Docker, go here: http://docs.docker.com/installation/

To run the VM, execute this:
```bash
CID=$(docker run -d nicopace/ionic-cordova-android-vagrant-)
```

to go inside the VM:
```bash
IP=$(docker inspect --format '{{ .NetworkSettings.IPAddress }}' $CID)
ssh app@$IP # password: app
```

Inside the VM, you have all the tools to work with... for example:
```bash
PROJECT=https://github.com/nicopace/congress-mobile.git
PROJECT_NAME=congress-mobile
git clone $PROJECT
cd $PROJECT_NAME
ionic serve
```

The image also has support for connected USB Android devices.
In order to have access to usb devices, you have to run the image in privileged mode.
To do so, add the parameter '-privileged' to the run command.
It should be:

```bash
$ CID=$(docker run -d nicopace/ionic-cordova-android-vagrant-)
```

If that does not work, or shows `????? permissions`, then run:

```bash
sudo /opt/android-sdk-linux/platform-tools/adb kill-server
sudo /opt/android-sdk-linux/platform-tools/adb start-server
```
