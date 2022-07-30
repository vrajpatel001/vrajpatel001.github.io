---
title: "OpenROAD Setup"
description: "Required Dependencies"
---

#### Update the existing Linux package
```bash
sudo apt-get update
sudo apt-get upgrade
```

#### Clone the OpenROAD repository
```bash
git clone --recursive https://github.com/The-OpenROAD-Project/OpenROAD.git
```

#### Follow their tutorial with this page
```html
https://openroad.readthedocs.io/en/latest/user/BuildLocally.html
```

#### Install the dependencies (For OpenROAD GUI)
```bash
sudo apt-get install qtcreator
sudo apt-get install qtbase5-dev qt5-qmake cmake
```

#### Install the dependencies (For running cmake)
```bash
sudo apt-get install swig
sudo apt-get install libboost-all-dev
sudo apt-get install libspdlog-dev
sudo apt-get install bison
sudo apt-get install flex
sudo apt-get install libeigen3-dev
sudo apt-get install liblemon-dev
```

#### View the output log
```bash
sudo ./etc/DependencyInstaller.sh -dev 2>&1 | tee output.log
```

#### Install the dependencies (For running make)
```bash
sudo apt-get install libreadline-dev
sudo apt-get install tcl-dev
sudo apt-get install libffi-dev
```

#### Note
- Once tcl-dev package is installed, one might then possibly come across the code expecting tcl.h to be in /usr/include/, but in order to facilitate multiple versions of tcl being installed, Linux places tcl.h in /usr/include/tcl/ i.e., one extra directory level.
- Replacing '#include <tcl.h>' with '#include <tcl/tcl.h>' in the source code for the build should get around this.
- For installing klayout follow their official document.

#### For changing path of tcl library in source file
```bash
$sed -i 's+<tcl.h>+<tcl/tcl.h>+g' filepath
```

#### For more information visit the below URLs'
```html
https://ubuntuhandbook.org/index.php/2020/07/install-qt4-ubuntu-20-04/
https://github.com/KLayout/klayout/issues/131
https://gist.github.com/flaport/ad2bf1cab692bdd12484d64065ca0b5c
https://github.com/KLayout/klayout
https://github.com/The-OpenROAD-Project/OpenROAD/issues/1061
https://askubuntu.com/questions/1404263/how-do-you-install-qt-on-ubuntu22-04
https://stackoverflow.com/questions/69828508/warning-ignoring-xdg-session-type-wayland-on-gnome-use-qt-qpa-platform-wayland
```