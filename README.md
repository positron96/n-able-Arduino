# n-able Arduino core

An Arduino Core for ARM based BLE boards supported by the NimBLE stack.

If you are interested in assisting the development of this project please submit issues and PR's. Or become a collaborator!

## Features

* Fully supports the [NimBLE-Arduino](https://github.com/h2zero/NimBLE-Arduino) library on Arm based BLE devices (only Nordic mcu's for now)
* No softdevice, NimBLE provides a complete BLE stack.
* Contains a subset of the EEPROM library to support basic config storage in flash.
* Supports `printf` and `Serial.printf`
* Uses/includes FreeRTOS.
* Designed to maximize battery life using tickless idle. This allows the MCU to sleep any time `delay` is called.
* Custom configuration of FreeRTOS and NimBLE compile options supported by providing a `build_opt.h` file in your sketch.

## Why?

I wanted to have a consistent BLE API on all of the devices I work with. NimBLE is the best choice for this as it is the most feature complete and fully open source library available for Arduino.

## Supported boards

### nRF52840
 * [Generic nRF52840 MCU](https://www.nordicsemi.com/Products/nRF52840)
 * [Nordic nRF52840 DK](https://www.nordicsemi.com/Products/Development-hardware/nRF52840-DK)
 * [Nordic nRF52840 Dongle](https://www.nordicsemi.com/Products/Development-hardware/nrf52840-dongle)
 * [Adafruit CLUE nRF52840](https://www.adafruit.com/product/4500)
 * [Adafruit Circuit Playground Bluefruit](https://www.adafruit.com/product/4333)
 * [Adafruit Feather nRF52840 Express](https://www.adafruit.com/product/4062)
 * [Adafruit Feather nRF52840 Sense](https://www.adafruit.com/product/4516)
 * [Adafruit ItsyBitsy nRF52840 Express](https://www.adafruit.com/product/4481)
 * [Ebyte E104-BT5040U](https://www.ebyte.com/en/product-view-news.html?id=1185)

### nRF52833
 * [Generic nRF52833 MCU](https://www.nordicsemi.com/Products/nRF52833)
 * [Nordic nRF52833 DK](https://www.nordicsemi.com/Products/Development-hardware/nRF52833-DK)
 * [BBC micro:bit v2](https://microbit.org/new-microbit/)

### nRF52832
 * [Generic nRF52832 MCU](https://www.nordicsemi.com/Products/nRF52832)
 * [Nordic nRF52832 DK](https://www.nordicsemi.com/eng/Products/Bluetooth-Smart-Bluetooth-low-energy/nRF52-DK)
 * [RedBear Blend 2](https://github.com/redbear/nRF5x#blend-2)
 * [RedBear Nano 2](https://github.com/redbear/nRF5x#ble-nano-2)
 * [Bluey](https://github.com/electronut/ElectronutLabs-bluey)
 * [hackaBLE](https://github.com/electronut/ElectronutLabs-hackaBLE)
 * [hackaBLE_v2](https://github.com/electronut/ElectronutLabs-hackaBLE)
 * [Adafruit Feather nRF52832](https://www.adafruit.com/product/3406)
 * [Ebyte E104-BT5032A-TB](https://www.ebyte.com/en/product-view-news.html?id=956)

### nRF51
 * [Generic nRF51 MCU](https://www.nordicsemi.com/eng/Products/Bluetooth-low-energy/nRF51822)
 * [BBC micro:bit](https://microbit.org)
 * [Calliope mini](https://calliope.cc/en)
 * [Bluz DK](http://bluz.io)
 * Nordic Semiconductor  [nRF51822 Development Kit](https://www.nordicsemi.com/eng/Products/Bluetooth-low-energy/nRF51822-Development-Kit)
 * [Nordic Semiconductor NRF51 Smart Beacon Kit](https://www.nordicsemi.com/eng/Products/Bluetooth-low-energy/nRF51822-Bluetooth-Smart-Beacon-Kit)
 * [Nordic Semiconductor NRF51 Dongle](http://www.nordicsemi.com/eng/Products/nRF51-Dongle)
 * [OSHChip](http://www.oshchip.org/)
 * [RedBearLab BLE Nano](http://redbearlab.com/blenano/)
 * [RedBearLab nRF51822](http://redbearlab.com/redbearlab-nrf51822/)
 * [Waveshare BLE400](http://www.waveshare.com/wiki/BLE400)
 * [ng-beacon](https://github.com/urish/ng-beacon)
 * [TinyBLE](https://www.seeedstudio.com/Seeed-Tiny-BLE-BLE-%2B-6DOF-Mbed-Platform-p-2268.html)
 * [Sino:bit](http://sinobit.org)

## Installing

### Board Manager

 1. [Download and install the Arduino IDE](https://www.arduino.cc/en/Main/Software) (At least v1.6.12)
 2. Start the Arduino IDE
 3. Go into Preferences
 4. Add ```https://h2zero.github.io/n-able-Arduino/package_n-able_boards_index.json``` as an "Additional Board Manager URL"
 5. Open the Boards Manager from the Tools -> Board menu and install "Arm BLE Boards"
 6. Select your board from the Tools -> Board menu

### From git (for core development)

 1. Follow steps from Board Manager section above
 2. ```cd <SKETCHBOOK>```, where ```<SKETCHBOOK>``` is your Arduino Sketch folder:
  * OS X: ```~/Documents/Arduino```
  * Linux: ```~/Arduino```
  * Windows: ```~/Documents/Arduino```
 3. Create a folder named ```hardware```, if it does not exist, and change directories to it
 4. Clone this repo: ```git clone https://github.com/h2zero/n-able-Arduino.git```
 5. Restart the Arduino IDE

## Flashing your device

1. Select your board from the Tools -> Board menu
2. Select any options you want
3. Select a programmer (J-Link, ST-Link V2, CMSIS-DAP, Black Magic Probe, adafruit-nrfutil or nrfutil) from the Tools -> "Programmer: " menu
4. Connect your programmer to the device and click Upload

### Uploading via Segger J-Link
 1. Make sure you have [Segger J-Link](https://www.segger.com/downloads/jlink) installed on your system.
 2. (For Windows) add the JLink.exe path to your environment variables.
 3. Select J-Link as the firmware uploader in the tools menu.

### Uploading via adafruit-nrfutil (for Adafruit bootloader devices only)
 1. Install adafruit-nrfutil if not already installed `pip install adafruit-nrfutil`
 2. Select adafruit-nrfutil as the firmware uploader in the tools menu.

### Uploading via (Nordic) nrfutil (for Nordic bootloader devices only)
 1. Install nrfutil if not already installed `pip install nrfutil`
 2. Select nrfutil as the firmware uploader in the tools menu.

## BLE

This Arduino Core does **not** contain any BLE functionality. It has been designed to support using the [NimBLE-Arduino](https://github.com/h2zero/NimBLE-Arduino) library for BLE operation.
**Note:** Currently only the release version 1.4.0 and above of [NimBLE-Arduino](https://github.com/h2zero/NimBLE-Arduino) supports Arm devices.

## Bootloader
Currently only some boards have Adafruit bootloaders available which are provided as options. You may choose to use the bootloader or none.  
The provided Adafruit bootloaders have no softdevice, if you currently are using the softdevice based Adafruit bootloader on your nRF52 board you will need to update it to the one provided by selecting it from the boards menu and clicking `Burn Bootloader`.

For boards without the Adafruit bootloader option clicking `Burn Bootloader` will simply erase the flash memory on the device. This is required if you have any bootloader flashed already.

## Credits

This core is based on [Arduino-nRF5](https://github.com/sandeepmistry/arduino-nRF5) by Sandeep Mistry,
which is based on the [Arduino SAMD Core](https://github.com/arduino/ArduinoCore-samd).
With some code from [Adafruit_nRF52_Arduino](https://github.com/adafruit/Adafruit_nRF52_Arduino)

The following libraries are used:

- [FreeRTOS](https://www.freertos.org/) as operating system
- [nrfx](https://github.com/NordicSemiconductor/nrfx) for peripherals driver
- [TinyUSB](https://github.com/hathach/tinyusb) as usb stack
