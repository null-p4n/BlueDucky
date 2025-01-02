# BlueDucky Ver 2.2

<p align="center">
  <img src="./images/duckmenu.png">
</p>

🚨 CVE-2023-45866 - BlueDucky Implementation (Using DuckyScript)

🔓 Unauthenticated Peering Leading to Code Execution (Using HID Keyboard)

<p align="center">
  <img src="./images/BlueDucky.gif">
</p>

BlueDucky v2.2
--------------

A powerful Bluetooth HID attack tool that emulates keyboard input through Bluetooth connections, based on the original keystroke-injection-android-linux project.

Features
--------

Core Functionality

-   Bluetooth HID keyboard emulation
-   DuckyScript payload support
-   Interactive device selection
-   Automatic reconnection handling
-   Color-coded logging system

Technical Features

-   L2CAP connection management (SDP, HID Control, HID Interrupt)
-   SSP (Secure Simple Pairing) support
-   NoInputNoOutput pairing agent
-   Comprehensive error handling
-   Automatic device cleanup

Requirements
------------

-   Python 3.x
-   Linux-based system
-   BlueZ tools
-   Root privileges
-   Required Python packages:

    -   pydbus
    -   bluetooth
    -   argparse

Installation
------------

bash

`git clone https://github.com/null-p4n/BlueDucky cd BlueDucky pip3 install -r requirements.txt `

Usage
-----

bash

`sudo python3 BlueDucky.py --adapter hci0 `

Payload Structure
-----------------

Payloads are stored in the `payloads/` directory and support the following commands:Basic Commands

-   STRING: Types the specified text
-   DELAY: Waits specified milliseconds
-   TAB: Sends Tab key
-   ENTER: Sends Enter key

Special Commands

-   PRIVATE_BROWSER: Opens private browsing
-   VOLUME_UP: Increases system volume
-   Modifier combinations (CTRL, ALT, SHIFT, GUI)

Key Improvements in v2.2
------------------------

Core Changes

-   Enhanced Bluetooth initialization sequence
-   Improved agent registration process
-   Better device pairing management
-   Robust error handling
-   Automatic device cleanup

New Features

-   Interactive payload selection
-   Enhanced logging system
-   Better device targeting
-   Improved character mapping
-   Support for special key combinations

Contributing
------------

1.  Fork the repository
2.  Create your feature branch
3.  Commit your changes
4.  Push to the branch
5.  Create a Pull Request

License
-------

This project is licensed under the MIT License - see the LICENSE file for details.

Acknowledgments
---------------

Based on the original keystroke-injection-android-linux project with significant enhancements and new features.

Disclaimer
----------

This tool is for educational purposes only. Users are responsible for obtaining proper authorization before testing on any devices.

## Installation and Usage 🛠️

### Setup Instructions for Debian-based 

```bash
# update apt
sudo apt-get update
sudo apt-get -y upgrade

# install dependencies from apt
sudo apt install -y bluez-tools bluez-hcidump libbluetooth-dev \
                    git gcc python3-pip python3-setuptools \
                    python3-pydbus

# install pybluez from source
git clone https://github.com/pybluez/pybluez.git
cd pybluez
sudo python3 setup.py install

# build bdaddr from the bluez source
cd ~/
git clone --depth=1 https://github.com/bluez/bluez.git
gcc -o bdaddr ~/bluez/tools/bdaddr.c ~/bluez/src/oui.c -I ~/bluez -lbluetooth
sudo cp bdaddr /usr/local/bin/
```

```bash
# Install dependencies
sudo apt update
# install dependencies from apt

sudo apt install -y bluez-tools bluez-hcidump libbluetooth-dev git gcc python3-pip python3-setuptools python3-pydbus

install pybluez from source

git clone https://github.com/pybluez/pybluez.git
cd pybluez
sudo python3 setup.py install

Next, we need to build bdaddr from source. bdaddr enables us to query or set the local Bluetooth device address.

cd ../
git clone — depth=1 https://github.com/bluez/bluez.git
gcc -o bdaddr ~/bluez/tools/bdaddr.c ~/bluez/src/oui.c -I ~/bluez -lbluetooth
sudo cp bdaddr /usr/local/bin/

Install Blueduckky

git clone https://github.com/pentestfunctions/BlueDucky.git
cd BlueDucky

To start the bluetooth in linux hit the below command

sudo hciconfig hci0 up
```

### Setup Instructions for Arch-based 

```bash
# update pacman & packages
sudo pacman -Syyu

# install dependencies
# since arch doesn't separate lib packages: libbluetooth-dev included in bluez package
sudo pacman -S bluez-tools bluez-utils bluez-deprecated-tools \
               python-setuptools python-pydbus python-dbus
               git gcc python-pip \

# install pybluez from source
git clone https://github.com/pybluez/pybluez.git
cd pybluez
sudo python3 setup.py install

# build bdaddr from the bluez source
cd ~/
git clone --depth=1 https://github.com/bluez/bluez.git
gcc -o bdaddr ~/bluez/tools/bdaddr.c ~/bluez/src/oui.c -I ~/bluez -lbluetooth
sudo cp bdaddr /usr/local/bin/
```

## Running BlueDucky
```bash
git clone https://github.com/pentestfunctions/BlueDucky.git
cd BlueDucky
sudo hciconfig hci0 up
python3 BlueDucky1.py --adapter hci0
```

alternatively,

```bash
pip3 install -r requirements.txt
```


#### 📝 Example payload.txt:
```bash
REM Title of the payload
STRING ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz1234567890!@#$%^&*()_-=+\|[{]};:'",<.>/?
GUI D
```

```bash
REM Opens a private browser to hackertyper.net
DELAY 200
ESCAPE
GUI d
ALT ESCAPE
GUI b
DELAY 700
REM PRIVATE_BROWSER is equal to CTRL + SHIFT + N
PRIVATE_BROWSER
DELAY 700
CTRL l
DELAY 300
STRING hackertyper.net
DELAY 300
ENTER
DELAY 300
```








