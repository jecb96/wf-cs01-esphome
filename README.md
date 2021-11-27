# (Etersky) WF-CS01 ESPHome Config

This repository contains a config template and usage example for [WF-SC01](https://templates.blakadder.com/WF-CS01_EU.html) like curtain switches to be used with ESPHome.
The author used a device distributed under the name "Etersky WF-CS01" with a `esp01_1m` like board.

⚠️ Be aware that you use this software at your own risk so the author can not be held accountable for any damage done or loss of functionality. (c.f. LICENSE) ⚠️

## Prerequisites

* A WF-SC01 like device
* A TTL UART adapter to flash the internal ESP8266
* Some wires
* Home Assistant with the ESPHome extension installed

## Create the ROM

1. Copy the files in `src/esphome` to your Home Assistant's `esphome` folder
2. Adapt the `concrete_device.yaml` to fit your cover
3. [Compile the ROM using ESPHome](https://esphome.io/guides/getting_started_hassio.html) and download the `.bin` file

## Flash the ROM

**Note: At the time of writing [Tuya Convert](https://github.com/ct-Open-Source/tuya-convert) did not work.**

To flash the included ESP8266, you can follow the guidelines on [Blakadder](https://templates.blakadder.com/WF-CS01_EU.html).
Hence, you may scratch/cut the RXD0 line on the PCB which can render the stop button useless. 

If the ESP8266 does not enter its flash mode, you may try the following:

1. Disconnect your TTL UART adapter from the device 
-> The ESP8266 must be without power
2. Connect `GPIO0` and `GND`
3. Connect your TTL UART adapter with the device
4. Disconnect `GPIO0` and `GND`

## Usage of the Hardware Switch after Flashing

After a successful flash you may use the switch as follows:

* To open/close the cover, touch the open/close button
* To stop the cover press, touch the same button again
* **The stop button is unused as the preparation step for manual flashing might have permanently destroyed its connection**
* The backlight can be turned on via Home Assistant