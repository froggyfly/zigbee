---
model: V3-BTZB  
vendor: Danalock
title: BT/ZB smartlock
category:
functions:  lock/unlock, battery
image: /assets/images/devices/V3-BTZB.jpg
compatible: [z2m]
mlink: 
link: 
link2: 
link3: 
---


#### Manual Home Assistant configuration
Although Home Assistant integration through [MQTT discovery](https://www.zigbee2mqtt.io/integration/home_assistant) is preferred,
manual integration is possible with the following configuration:


{% raw %}
```yaml
lock:
  - platform: "mqtt"
    state_topic: "zigbee2mqtt/<FRIENDLY_NAME>"
    availability_topic: "zigbee2mqtt/bridge/state"
    command_topic: "zigbee2mqtt/<FRIENDLY_NAME>/set"
    value_template: "{{ value_json.state }}"

sensor:
  - platform: "mqtt"
    state_topic: "zigbee2mqtt/<FRIENDLY_NAME>"
    availability_topic: "zigbee2mqtt/bridge/state"
    unit_of_measurement: "-"
    value_template: "{{ value_json.linkquality }}"
```
{% endraw %}

