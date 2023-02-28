# Frontend Example
The goal is to eventually have a custom lovelace card to display the sensor's information. In the meantime, a makeshift scoreboard can be created using template sensors. Follow the steps below to get a result similar to this:

## Current Info:

![Current Grill](./photos/minicurrent.jpg) 

Configuration for Current Card
```
square: true
columns: 4
type: grid
title: Current
cards:
  - type: tile
    entity: sensor.pellets
    vertical: true
  - type: tile
    entity: sensor.pelletlevel
    vertical: true
  - type: tile
    entity: sensor.pifire_mode
    show_entity_picture: false
    vertical: true
    icon: ''
    name: Mode
    color: primary
  - type: tile
    entity: sensor.grill_setpoint
    show_entity_picture: false
    vertical: true
    name: Grill Setpoint
    color: green
  - type: tile
    entity: sensor.grill_temp
    vertical: true
    show_entity_picture: false
    name: Grill Temp
    icon: mdi:grill-outline
    color: red
  - type: tile
    entity: sensor.probe1_temp
    vertical: true
    name: Probe 1
    icon: mdi:thermometer-probe
    color: red
  - type: tile
    entity: sensor.probe2_temp
    vertical: true
    name: Probe 2
    icon: mdi:thermometer-probe
    color: red
  - type: tile
    entity: automation.update_grill_when_on
    vertical: true
    icon: mdi:refresh
    color: yellow
    icon_tap_action:
      action: call-service
      service: automation.trigger
      data: {}
      target:
        entity_id: automation.update_grill_when_on
    name: Refresh

```

## Control Board:

![Control Board](./photos/minicontrol.jpg) 

Configuration for Control Card
```
square: true
columns: 4
type: grid
title: Controls
cards:
  - type: tile
    entity: input_select.grill_temp_setpoint
    vertical: true
    name: ' Set Temp/Hold'
    icon_tap_action:
      action: call-service
      service: rest_command.grillsettemp
      data: {}
      target: {}
    tap_action:
      action: call-service
      service: input_select.select_next
      data: {}
      target:
        entity_id: input_select.grill_temp_setpoint
  - type: tile
    entity: input_select.grill_mode_select
    vertical: true
    tap_action:
      action: call-service
      service: input_select.select_next
      data: {}
      target:
        entity_id: input_select.grill_mode_select
    icon: ''
    icon_tap_action:
      action: call-service
      service: rest_command.grillmodeandtemp
      data: {}
      target: {}
    name: Set Mode/Temp
  - type: tile
    entity: sensor.smoke_plus
    icon_tap_action:
      action: call-service
      service: rest_command.startsmokeplus
      data: {}
      target: {}
    show_entity_picture: false
    vertical: true
    tap_action:
      action: call-service
      service: rest_command.stopsmokeplus
      data: {}
      target: {}
  - type: tile
    entity: input_select.prime_amount
    show_entity_picture: false
    vertical: true
    icon_tap_action:
      action: call-service
      service: rest_command.grillprimeonly
      data: {}
      target: {}
    tap_action:
      action: call-service
      service: input_select.select_next
      data: {}
      target:
        entity_id: input_select.prime_amount
```
