# Raspberry-Pi

instructions for configuring Raspberry Pi Zero 2 w with docker running:
* Portainer
* AdGuard
* nginx
* certbot
* nginx proxy manager
* Heimdall

## Requirements

* Raspberry Pi Zero 2 w
* USB SD card reader adapter
* micro usb to usb for Power
* Zenmap software

## Configuration

* Using [Raspberry Pi Imager](https://www.raspberrypi.com/software/) boot [Raspberry Pi OS Lite](https://www.raspberrypi.com/software/operating-systems/#raspberry-pi-os-64-bit) and configure settings
    * (Optional) Setup WiFi on a Pi Manually using `wpa_supplicant.conf` by moving a file to :/boot

* Open nmap and Quick scan `nmap -T4 -A -v 192.168.5.0/24`
    * W8 few mi for RaspberryPi to boot
    * try to see if you can see if there is a IP and green light stoped flashing
    * Login to router and check	> Active clients to see hostname and IP address and MAC address


## Installation

SSH into pi `ssh pi@raspberrypi`.

Update OS `sudo apt update && sudo apt upgrade -y`

Reboot `sudo reboot`

Install docker `sudo apt install docker.io`

### Install Portainer with Docker on Linux

First, create the volume that Portainer Server will use to store its database:
* `docker volume create portainer_data`

Then, download and install the Portainer Server container:

```
docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ee:latest

```


### Useful links

https://docs.portainer.io/user/kubernetes

https://docs.docker.com/engine/install/ubuntu/  
https://docs.portainer.io/start/install/server/docker/linux

https://www.youtube.com/watch?v=vBgCZvCDFh8
https://www.youtube.com/watch?v=o7nn