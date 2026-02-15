# sat-com-com

**Satellite Communism Commander: Data wants to be free. Pull it down and give it to the people!**

`sat-com-com` is a `termbox2` CLI/TUI project for managing operations on specific recycled satellite hardware, centered on:

- Recycled robotic RV satellite dish
- Raspberry Pi Zero 2 W
- PiSugar 2 battery

## Parts List 
*You can support this project by clicking on these affiliate links which doesn't cost you anything.  *
*You can also [buy me a coffee](https://buymeacoffee.com/cjtrowbridge).*

- Recycled robotic RV satellite dish (motorized or fixed/manual)
- [Raspberry Pi Zero 2 W](https://amzn.to/45SZN9K)
- [PiSugar 2 battery](https://amzn.to/4aBLXer)
- [RTL-SDR dongle](https://amzn.to/4tk5M1i)
- [Filter+Amplifier](https://amzn.to/45TIxB9)
- Three options for feeds (satellite antennas):
  - [3D Print: The very good but very complicated helicone](https://www.thingiverse.com/thing:6436342/files)
  - [3d Print: My "ok" but very easy yagi](https://github.com/cjtrowbridge/DIY-Weather-Satellite-Uplink/blob/main/cad/out/yagi_card/yagi_card.stl)
  - [Buy a pre-made feed but it wont be robotic](https://amzn.to/4aqFSjJ)
- Cabling/adapters/power components as required by your build

## Overview

The basic RF hardware pipeline is:

`(custom feed option) -> (filter + amplifier) -> (sdr)`

The system must run `rtl_tcp` so other devices on the network can access SDR data.

## Project Goals

### 1) Initial Goal: Find either or both of the Geostationary GOES Weather Satellites

Facilitate locating either or both target geostationary satellites.

- If motor control is available:
  - Sweep the visible sky
  - Build an RSSI sky map
  - Select the strongest candidate automatically or let the user choose
- If motor control is not available (or dish is non-motorized):
  - Provide guided manual pointing with a live RSSI meter in the TUI
  - Walk users step-by-step through alignment

### 2) Continuous Data Pull + Local Distribution

Attempt to continuously pull data on-device and publish updates into an Apache-served directory for local users.

- This may be infeasible on constrained hardware (Pi Zero 2 W + power/storage limits)
- The implementation should be designed to degrade gracefully if full-time ingest cannot be sustained

### 3) Future Goal: Friendly Web Front End

If continuous ingest and local serving are stable, build a small web interface that:

- Highlights the most useful information first
- Links users to deeper/raw/technical data views

## Design Notes

- Motor control interface should be optional and modular.
- Manual pointing support is a first-class feature, not a fallback afterthought.
- Hardware variability is expected; not every dish has compatible motors or control electronics.
- TUI workflows should support both fully automated and mostly manual station operation.
- The web interface should at a minimum have information like battery status, current rssi, etc for basic monitoring without needing to ssh into the device.

## Related Projects

[https://github.com/saveitforparts/Carryout-Radio-Telescope](https://github.com/saveitforparts/Carryout-Radio-Telescope)) A similar project by saveitforparts which focuses primarily on scanning the sky for radio sources.