# ESPHome-sound-detector


https://thibmaek.com/posts/detecting-sound-level-using-esp8266-and-esphome!

[KY-038](https://user-images.githubusercontent.com/58307338/155599575-343adcfb-3294-41b6-9f58-004885b98063.png)



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
