# ESPHome-sound-detector

## Description:

[Tutorial](https://thibmaek.com/posts/detecting-sound-level-using-esp8266-and-esphome)

## Wiring:

![Wiring:](https://images.ctfassets.net/vzyw32ih2a4n/7JNQcx7KGhluEEglaWz36/6f296c7f23a5b752b22d4860d9776360/KY-038.png)

## ESPHome code:

```
esphome:
  name: wemos_sound_level_detector
  platform: ESP8266
  board: d1_mini

wifi:
  ssid: !secret wifi_ssid
  password: !secret wifi_password

logger:
ota:
api:

# BELOW WILL READ OUT THE ANALOG SIGNAL

# sensor:
  # - platform: adc
  #   pin: A0
  #   name: "Sound level"
  #   update_interval: 1s
  #   filters:
  #     - multiply: 3.3 # see https://esphome.io/components/sensor/adc.html

# DEBOUNCED FOR 1S BECAUSE THE TRIGGER PERIOD IS VERY SHORT

binary_sensor:
  - platform: gpio
    pin: D2
    name: "Sound level"
    filters:
      - delayed_off: 1s
```
