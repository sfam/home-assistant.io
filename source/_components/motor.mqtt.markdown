---
layout: component
title: "MQTT Motor"
description: "Instructions how to integrate MQTT motorized devices into Home Assistant."
date: 2015-12-01 12:00
sidebar: true
comments: false
sharing: true
footer: true
logo: mqtt.png
ha_category: Motor
---


This platform enables the possibility to control an MQTT motorized device. The device state will be updated only after receiving the a new state from `state_topic`. If these messages are published with RETAIN flag, the MQTT device will receive an instant state update after subscription and will start with correct state. Otherwise, the initial state will be `unknown`.
There is a state attribute that stores the relative position of the device, where 0% means the device is `closed` and all other intermediate positions means the device is `open`.

```yaml
# Example configuration.yaml entry
motor:
  platform: mqtt
  name: "Bedroom Rollershutter"
  state_topic: "home/bedroom/rollershutter"
  command_topic: "home/bedroom/rollershutter/set"
  qos: 0
  payload_open: "OPEN"
  payload_close: "CLOSE"
  payload_stop: "STOP"
```

Configuration variables:

- **command_topic** (*Required*): The MQTT topic to publish commands to control the motor.

- **name** (*Optional*): The name of the motorized device. Default is 'MQTT Motor'.
- **state_topic** (*Optional*): The MQTT topic subscribed to receive state updates. If not defined, the motor will be stateless, that is, no information about current position or open/closed. If defined, the received payload must be a integer between 0 and 100, that represents the percentage for fully closed and fully open, respectively.
- **qos** (*Optional*): The maximum QoS level of the state topic. Default is 0. This QoS will also be used to publishing messages.
- **payload_open** (*Optional*): The payload to open the motorized device. Default is "OPEN".
- **payload_close** (*Optional*): The payload to close the motorized device. Default is "CLOSE".
- **payload_stop** (*Optional*): The payload to stop the motorized device. Default is "STOP".
- **state_format** (*Optional*): The state format to parse. Default is None (no parser).

