# ClockMcClockington
I currently have some “Lenovo Smart Clock Essentials” around the house, but they’ll need to be returned to the original owner soon. Essentially they’re just a segment display with some smarts and a microphone for Google Home.

I’m no fan of voice assistance, so the microphone has been off, meaning they don’t provide much real world value for me other than a clock and that should be easy enough to replicate with an ESP32 and ESPHome.

Since all of the smarts in my house run off Home Assistant (HA), I want this clock to be able to interact with HA. Specifically, I want some buttons that can then trigger other things in the house, such as “shut down all the lights”, or “volume up/down” for the bedroom Sonos speakers. That way I don’t need to have my phone on.

## Hardware
* WeMos S2 Mini (ESP32-S2)
* MAX7219 8x32 Dot LED Matrix 
* (4) TPP223 touch sensor
* 10k ohm resistor
* GL5516 LDR Photoresistor
* ClockMcClockington PCB
  
## Software
TODO: 
ESPHome

## Shell
TODO: 

## Circuit
TODO:
![PXL_20260126_025301969 PORTRAIT](https://github.com/user-attachments/assets/266d4dd0-680c-46d8-819b-79539a51083d)
