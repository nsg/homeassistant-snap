# homeassistant-nsg
[![Snap Status](https://build.snapcraft.io/badge/nsg/homeassistant-snap.svg)](https://build.snapcraft.io/user/nsg/homeassistant-snap)

A snap packaging [Home Assistant](https://home-assistant.io). Home Assistant is an open-source home automation platform running on Python 3. Track and control all devices at home and automate control.

`homeassistant-nsg` is an unofficial snap that packages the code from the [official Git repository at GitHub](https://github.com/home-assistant/home-assistant).

## About this package

I build this for my needs, I liked to setup an installation based around Home Assistant and snaps are a nice atomic way for me to deploy and manage applications.

Feel free to open an issue, or create a pull request if you like to contribute.

## Install

My home system follows the edge channel (`snap install --edge homeassistant-nsg`). If a
build works for me, I will publish it to stable.

## Tellstick

I have a TellStick Duo running on a secondary host, that shares a private network with
the container running this snap. I expose the sockets at `/tmp/Telldus{Client,Events}`
over the network with these unit-files:

```
[Unit]
Description=Expose Telldus sockets over TCP
After=network.target

[Service]
ExecStart=/usr/bin/socat TCP-LISTEN:50801,reuseaddr,fork,bind=192.168.40.2 UNIX-CONNECT:/tmp/TelldusEvents
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

```
[Unit]
Description=Expose Telldus sockets over TCP
After=network.target

[Service]
ExecStart=/usr/bin/socat TCP-LISTEN:50800,reuseaddr,fork,bind=192.168.40.2 UNIX-CONNECT:/tmp/TelldusClient
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

The Home Assistant configuration is then:

```
tellstick:
  host: 192.168.40.2
  port: [50800, 50801]
```
