---
layout: post
title:  Set up shadowsocks service on ubuntu
date:   2020-02-23 10:00:00 +0800
tags: VPN
---
Here is a tutorial of setting up shadowsocks service on VPS with Ubuntu operation system.

## Prerequisites
1. A VPS.
2. Install Ubuntu 17.10 or above on the VPS

## Install Shadowsocks-libev Server
Install _shadowsocks-libev_ to Ubuntu
```bash
sudo apt update
sudo apt install shadowsocks-libev
```

## Modify Configuration File
After installation, edit the configuration file under path _/etc/shadowsocks-libev/_
```bash
sudo nano /etc/shadowsocks-libev/config.json
```
Nano is a text editor on Ubuntu, save the file as backup (Alt+B) after modification. Vi should be fine as well, but meet trouble with sudo. Still not sure if it is necessary to modify the configuration file with sudo.

The Default contents of the _config.json_ looks like following:
```bash
{
 "server":"127.0.0.1",
 "server_port":8388,
 "local_port":1080,
 "password":"focobguph",
 "timeout":60,
 "method":"chacha20-ietf-poly1305"
}
```
Replace _127.0.0.1_ with the public IP address of your VPS and change the _8388_ of the _server_port_ to other port number but don't use port_8388_ or the port you login to your VPS. Then set your preferred password which is used to encrypt traffic. You can leave the _method_ to default or change to other encryption method as you wish.

The contents may have some difference on difference version of Ubuntu, but the modification should be the same with described above.

## Start Service
Start shadowsocks-libev service by following command
```bash
sudo systemctl start shadowsocks-libev.service
```
Enable auto-start boot time.
```bash
sudo systemctl enable shadowsocks-libev.service
```
On Ubuntu 17.10, Shadowsocks-libev will automatically start with the default configuration file. It is needed to restart it to let your configurations take effect.
```bash
sudo systemctl restart shadowsocks-libev
```
Sometimes you may encounter the following error:
_This system doesn't provide enough entropy to quickly generate high-quality random numbers. The service will not start until enough entropy has been collected._
To fix this, you can install _rng-tools_.
```bash
sudo apt-get install rng-tools
sudo rngd -r /dev/urandom
```
Then try to restart the Shadowsocks-libev service again.
Check its status to make sure the service is running.
```bash
systemctl status shadowsocks-libev.service
```

## Reference
1. ___Xiao Guoan - [How to Set up Shadowsocks-libev Proxy Server on Ubuntu 16.04/17.10](https://www.linuxbabe.com/ubuntu/shadowsocks-libev-proxy-server-ubuntu-16-04-17-10)___
