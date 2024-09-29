# altserverpi0

The error kept persisting and being constant so I left my Pi running overnight and I woke up to (Adding Device ********-************** and Removing Device ********-**************) Messages

Tried to refresh my apps wirelessly and sure enough it just worked. I still see the error show up sometimes in the terminal window but rarely and when I go to refresh it works.


Follow these in Order for Best Results


Flash the Ubuntu 64bit Image to the Pi

Boot up and Configure Wifi

Configure so the machine Doesn't sleep and lock up automatically

Open Terminal and run (sudo apt update) then (sudo apt upgrade)

Install SSH Server (sudo apt install openssh-server) [Optionally check if its running (sudo systemctl status ssh)]

Install and Configure Python 3: (sudo apt install python3) [Fix Python Path error with (alias python='python3') then run (sudo ln -s /usr/bin/python3 /usr/bin/python)

Install libplist Manually https://github.com/libimobiledevice/libplist

Intall libimobiledevice-glue Manually https://github.com/libimobiledevice/libimobiledevice-glue#debian--ubuntu-linux

Install libusbmuxd Manually https://github.com/libimobiledevice/libusbmuxd [Remove the (libimobiledevice-glue-dev \) line from the first command for it to work]

Install libimobiledevice Manually https://github.com/libimobiledevice/libimobiledevice [Remove the (libimobiledevice-glue-dev \) line from the first command for it to work]

Install libirecovery Manually https://github.com/libimobiledevice/libirecovery [Remove the (libimobiledevice-glue-dev \) line from the first command for it to work]

Install idevicerestore Manually https://github.com/libimobiledevice/idevicerestore [Remove the (libimobiledevice-glue-dev \) line from the first command for it to work]

Install Docker (curl -sSL https://get.docker.com/ | sudo sh)


Install the Anisette Server Docker Image (Pick the Compatible one with your System Architecture)


(Arm Compatible)

(sudo docker pull ghcr.io/jkcoxson/netmuxd:latest)

(sudo docker pull ghcr.io/zeyugao/netmuxd:latest@sha256:08dc2ef2aafa41d8d69c3b27872430e7b12079d3e345038c4a94918a4c5289a8)


(x86 Compatible)

(sudo docker pull nyamisty/alt_anisette_server)

(sudo docker run -d --rm -p 6969:6969 -it nyamisty/alt_anisette_server)



Install these Items and their Dependencies


(sudo apt install idevicerestore) (apperantly on ubuntu its just avaliable)

(sudo apt-get install usbmuxd libimobiledevice6 libimobiledevice-utils)

(sudo apt-get install wget curl libavahi-compat-libdnssd-dev)

(sudo apt install usbmuxd)

(sudo apt install ninja-build)

(sudo apt install ldc)

(sudo apt install libimobiledevice-dev) (your distro might have this and skips manually building this earlier)

(sudo apt install libgtk-3-0)

(sudo apt install dub)

(sudo apt install libusbmuxd-dev)

(sudo apt install openssl)


(curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh) (On Ubuntu 64bit just did a normal install without any changes and it worked with rustc working)

(On Rasbian 32bit Customize Installation and Change Default Host Triple to (arm-unknown-linux-gnueabihf)



Run these Commands


(systemctl enable avahi-daemon.service)

(systemctl enable avahi-daemon.socket)

(systemctl start avahi-daemon.service)

(systemctl start avahi-daemon.socket)


(sudo systemctl restart avahi-daemon)

(sudo killall -s SIGKILL altserver usbmuxd netmuxd)

(sudo usbmuxd)


Now plug in the iDevice


(idevicepair pair) [You should see a (Success: Paired with ********-**************) (*'s being numbers)

(sudo kill -9 $(pidof usbmuxd)


At this point you can unplug and finally run AltServer Itself


(curl https://raw.githubusercontent.com/powenn/AltServer-Linux-PyScript/rewrite/main.py > main.py)

(python3 main.py)


Now you are up and running AltServer on you Raspberry Pi/Linux Box

Install the AltStore IPA to your device and enjoy wireless syncing



Thanks to this son of a bitch for making this shit for linux and anisette server: https://github.com/NyaMisty/AltServer-Linux

Thanks to this son of a bitch for making this shit wifi sync: https://github.com/jkcoxson/netmuxd

Special Thanks to this son of a bitch for making a nice and easy install python script: https://github.com/powenn/AltServer-Linux-PyScript

Special Thanks to this son of a bitch for making a GUI: https://github.com/powenn/AltServer-LinuxGUI

Fuck you for not having a Linux version JKJK Thanks for Altserver and Altstore: https://github.com/altstoreio/AltStore
