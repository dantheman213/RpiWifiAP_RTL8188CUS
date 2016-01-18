# Setup Raspberry Pi WiFi AP (with or without Internet connection)

This readme and scripts will help you get bootstrapped on using your Raspberry Pi 2 with wireless dongles that use the RTL8188CUS chipset.

Specifically, the *Edimax EW-7811Un* dongle. Raspbian with kernel 4.0+ has poor support for these chipsets.

Goal: Compile and setup software necessary to turn Pi into wireless router with said dongle.

### Provision ###

run raspi-config
-> expand filesystem

#### Update System ####
apt-get update

apt-get upgrade

#### Install necessary dependencies ####
apt-get install screen git dnsmasq haveged build-essential fakeroot devscripts debhelper libnl-dev libssl-dev

git clone https://github.com/jekader/hostapd-rtl.git

cd hostapd-rtl

bash build.sh

dpkg -i ../hostapd-rtl_2.4-4_armhf.deb


### Place config files ###

* dnsmasq.conf -> /etc/dnsmasq.conf
* hostapd.conf -> /etc/hostapd/hostapd.conf
* interfaces -> /etc/network/interfaces
* startAP -> /usr/sbin/startAP

### Run AP ###

just hit "startAP" into your command-line to run manually.

### Start on boot (optional) ###

append to but before last 'exit' line
/etc/rc.local

sudo /usr/sbin/startAP
