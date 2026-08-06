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
The ESPHome configuration is available as the [yaml file](https://github.com/TemuWolverine/ClockMcClockington/blob/main/clock.yaml), or as a [binary you can flash directly from your browser](https://temuwolverine.github.io/ClockMcClockington/)

### Setup
The temperature information is fetched from Home Assistant. You'll need to have the sensor preconfigured.

* Setup a template sensor
* Navigate (in Home Assistant) to Settings > Devices & Services > Helpers
* Create Helper (bottom right corner) > Template > Sensor
* Two fields are required, the name and the state. Name must be `clock_temp`
* Set the state to `{{ states("sensor.myweathersensor_temperature")}}`
  The other fields are entirely optional, but can make presentation in HomeAssistant clearer 

Alternatively, you can edit the YAML, change `weatherSensor : sensor.clock_temp` to `weatherSensor : sensor.sensor.myweathersensor_temperature`


### Automations
The way ESPHome exposes hardware buttons to Home Assistant is a bit funky (or I'm an idiot and have done it wrong) - they're exposed as generic events rather than 'click'.

ClockMcClockington sends out `esphome.<name>.clock_button_pressed`, where name will start with 'clockmcclockington' plus the MAC of the device. The event data will be one, two, three or four. Currently long press and double click are not implemented. 
```
alias: btnOne
description: ""
triggers:
  - trigger: event
    event_data:
      button: one
    event_type: esphome.clockmcclockingtonred.clock_button_pressed
conditions: []
actions:
  - action: light.toggle
    metadata: {}
    target:
      area_id: study
    data: {}
mode: single
```

## Shell
TODO: 

## Circuit
The Kicad project for the circuit design is available under the [/circuit](https://github.com/TemuWolverine/ClockMcClockington/tree/main/circuit) folder
<img width="1521" height="554" alt="image" src="https://github.com/user-attachments/assets/2ca5430a-0554-4252-a7c4-acba82484d5b" />

