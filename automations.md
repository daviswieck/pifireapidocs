## Force Update on initial change :

```
alias: Update pifire on start
description: ""
trigger:
  - platform: event
    event_type: call_service
    event_data:
      domain: rest_command
      service: grillprimeonly
      service_data: {}
  - platform: event
    event_type: call_service
    event_data:
      domain: rest_command
      service: grillsmoke
      service_data: {}
  - platform: event
    event_type: call_service
    event_data:
      domain: rest_command
      service: grillstartup
      service_data: {}
  - platform: event
    event_type: call_service
    event_data:
      domain: rest_command
      service: grillholdtemp
      service_data: {}
  - platform: event
    event_type: call_service
    event_data:
      domain: rest_command
      service: grillprimeandstartup
      service_data: {}
condition: []
action:
  - service: homeassistant.update_entity
    data: {}
    target:
      entity_id:
        - sensor.current_setpoints
        - sensor.current_status
        - sensor.current_temperature
mode: single
```
## Force Update when running any mode except "Stop" :
```
alias: Update grill when on
description: ""
trigger:
  - platform: time_pattern
    seconds: "3"
condition:
  - condition: not
    conditions:
      - condition: state
        entity_id: sensor.pifire_mode
        state: Stop
action:
  - service: homeassistant.update_entity
    data: {}
    target:
      entity_id:
        - sensor.current_setpoints
        - sensor.current_status
        - sensor.current_temperature
mode: single
```

## Notify Mobile App on Probe 1 Certain Temps :
```
alias: Notify Probe1 Temp
description: ""
trigger:
  - platform: state
    entity_id:
      - sensor.probe1_temp
    to:
      - "100"
      - "120"
      - "130"
      - "140"
      - "150"
      - "165"
      - "203"
condition: []
action:
  - device_id: 
    domain: mobile_app
    type: notify
    message: |-
      {% if is_state('sensor.probe1_temp', '100') %}
        Probe 1 temperature is now {{ states('sensor.probe1_temp') }}°F 
      {% elif is_state('sensor.probe1_temp', '120') %}
        Probe 1 temperature is now {{ states('sensor.probe1_temp') }}°F
      Pull for Rare! 
      {% elif is_state('sensor.probe1_temp', '130') %}
        Probe 1 temperature is now {{ states('sensor.probe1_temp') }}°F
      Pull for Medium-Rare! 
      {% elif is_state('sensor.probe1_temp', '140') %}
        Probe 1 temperature is now {{ states('sensor.probe1_temp') }}°F
      Pull for Medium! 
      {% elif is_state('sensor.probe1_temp', '150') %}
        Probe 1 temperature is now {{ states('sensor.probe1_temp') }}°F 
      Pull for Well Done!
      {% elif is_state('sensor.probe1_temp', '165') %}
        Probe 1 temperature is now {{ states('sensor.probe1_temp') }}°F 
      Pull and Wrap! 
      {% elif is_state('sensor.probe1_temp', '203') %}
        Probe 1 temperature is now {{ states('sensor.probe1_temp') }}°F 
      Pull Brisket and Rest!
      {% endif %}
mode: single
```

## Notify Mobile App on Probe 2 Certain Temps :
```
alias: Notify Probe2 Temp
description: ""
trigger:
  - platform: state
    entity_id:
      - sensor.probe2_temp
    to:
      - "100"
      - "120"
      - "130"
      - "140"
      - "150"
      - "165"
      - "203"
condition: []
action:
  - device_id: 
    domain: mobile_app
    type: notify
    message: |-
      {% if is_state('sensor.probe2_temp', '100') %}
        Probe 2 temperature is now {{ states('sensor.probe2_temp') }}°F
      {% elif is_state('sensor.probe2_temp', '120') %}
        Probe 2 temperature is now {{ states('sensor.probe2_temp') }}°F
      Pull for Rare! 
      {% elif is_state('sensor.probe2_temp', '130') %}
        Probe 2 temperature is now {{ states('sensor.probe2_temp') }}°F
      Pull for Medium-Rare! 
      {% elif is_state('sensor.probe2_temp', '140') %}
        Probe 2 temperature is now {{ states('sensor.probe2_temp') }}°F
      Pull for Medium! 
      {% elif is_state('sensor.probe2_temp', '150') %}
        Probe 2 temperature is now {{ states('sensor.probe2_temp') }}°F
      Pull for Well Done! 
      {% elif is_state('sensor.probe2_temp', '165') %}
        Probe 2 temperature is now {{ states('sensor.probe2_temp') }}°F
      Pull and Wrap! 
      {% elif is_state('sensor.probe2_temp', '203') %}
        Probe 2 temperature is now {{ states('sensor.probe2_temp') }}°F
      Pull Brisket and Rest!
      {% endif %}
mode: single
```
