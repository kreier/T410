# T410

[![MIT license](https://img.shields.io/github/license/kreier/T410?color=brightgreen)](https://kreier.mit-license.org/)

Project with Raspberry Pi 1B

<img src="https://raw.githubusercontent.com/kreier/T400/master/pic/T400lite.jpg" width='25%' align='right'>

## Hardware

We have a Raspberry Pi 1B from June 2012 with only the 26 pin on the GPIO header. On it a 480x320 3.5" display is mounted that needs a special driver. More on that in the Software section. It has only 2 USB2.0 ports. One for mouse/keyboard combo, the second for the TP-Link TL-WN725N WiFi dongle.

![Raspberry Pi with 3.5" display](RPi-T410.jpg)

## Software

Download the recent [Raspberry Pi OS](https://www.raspberrypi.org/software/) and install it on a SD card. I assume it is Raspbian Buster.

### Wifi

The WiFi dongle TP-Link TL-WN725N has the Realtek 8188eu chip on it that has only some old drivers in the repository that don't work. Following the recommendations from [MrEngman](http://downloads.fars-robotics.net/) you should edit the wpa_compliant file with

``` sh
me@rpi:~/ $ sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
```
and enter
```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=GB

network={
    ssid="Your-Network-Name"
    psk="Your-Network-Password"
}
```

Check your kernel version with ```uname -a```. Find and download the respective driver from the [fars-robotics.net](http://downloads.fars-robotics.net/wifi-drivers/8188eu-drivers/) website. Then unpack and install the driver:
``` sh
me@rpi:~/ $ tar xf 8188eu-your-kernel-version.tar.gz
me@rpi:~/ $ sudo ./install.sh
```
After reboot it should work.

### Display

For the display you need this driver:

http://www.lcdwiki.com/3.5inch_RPi_Display

## History

### Reactivated software - 2020/11/17

Download Raspbian OS from scratch. The regular graphical screen would not start, performed some tests on the browser. For example, the octane benchmark performed only 155 points.

### Initial idea

T410
2020/03/03

Initiated in March 2020, this robot car is powered by a Raspberry Pi 1B with 3.5 inch 480x320 display for 80x25 characters at the terminal. It needs 40 seconds to boot. Reactivated in November 2020.

See [at project aisvn](../aisvn).

