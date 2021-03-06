---
layout: component
title: "LimitlessLED"
description: "Instructions how to setup LimitlessLED within Home Assistant."
date: 2015-06-10 22:48
sidebar: true
comments: false
sharing: true
footer: true
ha_category: Light
---


The limitlessled platform can control your [LimitlessLED](http://www.limitlessled.com/) lights from within Home Assistant. The lights are also known as EasyBulb, AppLight, AppLamp, MiLight, LEDme, dekolight or iLight.

To add limitlessled to your installation, add the following to your `configuration.yaml` file:

```yaml
# Example configuration.yaml entry
light:
  platform: limitlessled
  host: IP_ADDRESS
  group_1_name: Living Room
  group_2_name: Bedroom
  group_3_name: Office
  group_4_name: Kitchen
```

Configuration variables:

- **host** (*Required*): IP address of the device, eg. 192.168.1.32
- **group_X_name** (*Required*): Name of the group. Multiple entries with a consecutive number.
