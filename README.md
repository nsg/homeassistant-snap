# homeassistant-nsg
[![Snap Status](https://build.snapcraft.io/badge/nsg/homeassistant-snap.svg)](https://build.snapcraft.io/user/nsg/homeassistant-snap)

A snap packaging [Home Assistant](https://home-assistant.io). Home Assistant is an open-source home automation platform running on Python 3. Track and control all devices at home and automate control.

`homeassistant-nsg` is an unofficial snap that packages the code from the [official Git repository at GitHub](https://github.com/home-assistant/home-assistant).

## About this package

I build this for my needs, I liked to setup an installation based around Home Assistant and snaps are a nice atomic way for me to deploy and manage applications.

Feel free to open an issue, or create a pull request if you like to contribute.

## Install

The latest stable is the version I'm using, and it works for me. To install it type `snap install homeassistant-nsg`.

The latest untested build directly from upstream rests in the edge channel, to try it type `snap install --edge homeassistant-nsg`.

To move between channels on an existing install, type `snap refresh --edge homeassistant-nsg` and so on.
