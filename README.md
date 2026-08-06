# ClockMcClockington
I currently have some “Lenovo Smart Clock Essentials” around the house, but they’ll need to be returned to the original owner soon. Essentially they’re just a segment display with some smarts and a microphone for Google Home.

I’m no fan of voice assistance, so the microphone has been off, meaning they don’t provide much real world value for me other than a clock and that should be easy enough to replicate with an ESP32 and ESPHome.

Since all of the smarts in my house run off Home Assistant (HA), I want this clock to be able to interact with HA. Specifically, I want some buttons that can then trigger other things in the house, such as “shut down all the lights”, or “volume up/down” for the bedroom Sonos speakers. That way I don’t need to have my phone on.

## BoM
| Part | Quantity | Note |
| -----| -------- | ---- |
| [ESP32-S3 Nano](https://s.click.aliexpress.com/e/_c4kUQqIB) | 1 | If you're using the ClockMcClockington PCB, it is designed for this specific ESP32. Otherwise, any S3 with 2MB of PSRAM should be fine |
| [5mm Tactile switches](https://s.click.aliexpress.com/e/_c4DqcA55) | 4 | |
| [GL5516 LDR Photoresistor](https://s.click.aliexpress.com/e/_c41f2RgX) | 1 | |
| [INMP441 Microphone](https://www.aliexpress.com/item/1005006090551057.html) | 1 | |
| [MAX98357a amplifier](https://www.aliexpress.com/item/1005006090551057.html) | 1 | |
| Speaker | 1 | |
|  0.1uf ceramic capacitor | 2| Decoupling, through-hole|
| 10k ohm resistor | 1 | Through-hole|
| ClockMcClockington PCB | 1 | Optional|

## Software
TODO: 
ESPHome


## Shell
TODO: 

## Circuit

