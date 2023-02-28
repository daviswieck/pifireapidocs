# Import Pifire Data in Home Assistant
Eventually I would like to make this a blueprint and make this a seamless integration, but for now this will have to do. 

# Beginning Steps
## First
I recommend adding a packages folder in your HA config folder to keep your main yaml as clean as possible. I did this under the "File editor". 
Create the folder then add the following to your configuration.yaml
```
homeassistant: 
    packages: !include_dir_named packages
```
## Second
Click on Settings->Devices & Services->Helpers(on the top tab)

Create the helpers included in the ![Helpers](./helpers.md) folder

## Third
Go back to File editor, navigate to your packages folder, and create the following two yaml's

pifire.yaml ![Import Data as Sensor](./yamls/pifire.yaml)

pifire_control.yaml ![Control Data](./yamls/pifire_controls.yaml)

In this file, be sure to change your IP address to whatever your Pifire instance is. 

Restart you HA instance and confirm your sensors have been properly created

## Fourth
Create the automations included in the ![Automations](./automations.md) folder

## Fifth
Test everything to make sure it works!

# API Info and States
### State
This is set in the "value_template:" yaml line. It can be anything you want. I like to set it as the current temperature of the grill. 

### Attributes
The table below lists which attributes are available in which states. 

### api/current
| Name | Description | Values | States |
| --- | --- | --- | --- |
| `Grill temp` | Current Temperature of Grill | | `Integer` |
| `Probe1 temp` | Current Temperature of Probe 1 | |  `Integer` |
| `Probe2 temp` | Current Temperature of Probe 2 | |  `Integer` |
| `Grill` | Grill's Setpoint. Set this to the temperature you want the grill to be. | | `Integer` |
| `Grill notify` | Grill's Notification Setpoint | |  `Integer` |
| `Probe1` | Probe 1's Notification Setpoint | | `Integer` |
| `Probe2` | Probe 2's Notification Setpoint | | `Integer` |
| `Mode` | Grill's Mode | `Stop` `Startup` `Smoke` `Hold` `Shutdown` `Prime` `Monitor` |
| `Name` | Grill's Friendly Name | | `String` |
| `Pelletlevel` | Grill's Pellet Level | | `Integer` |
| `Pellets` | Grill's Pellet Type | | `String` |
| `S plus` | Is the grill running Smoke Plus? | | `true` `false` |
| `Status` | Grill's Status | | `active` `null` |
| `Units` | Grill's Unit | | `F` `C` |

### api/control
| Name | Description | Values | States |
| --- | --- | --- | --- |
| `Distance update` | Update Pellet Distance Sensor | | `true` `false` |
| `Duty cycle` | ?????? | | `Integer` |
| `Errors` | ?????? | | `string` |
| `Hopper check` | ????? | | `INT` |
| `Manual` | Manual Control of | `auger` `change` `fan` `igniter` `power` `pwm` |  `true` `false` |
| `Mode` | Grill's Current Mode | `Stop` `Startup` `Smoke` `Hold` `Shutdown` `Prime` `Monitor` | |
| `Next Mode` | Grill's Next Mode | `Stop` `Startup` `Smoke` `Hold` `Shutdown` `Prime` `Monitor` |
| `Notify Data` | Change what the grill does when setpoints is reached | `hopper_low` `p1_keep_warm` `p1_shutdown` `p2_keep_warm` `p2_shutdown` `timer_keep_warn` `timer_shutdown` |  `true` `false` |
| `Notify req` | Notification request | `grill` `probe1` `probe2` `timer` |  `true` `false` |
| `Prime amount` | Amount of Pellets you want to prime in grams | | `Integer` | 
| `Probe profile update` | ?????? | | `true` `false` |
| `PWM control` | ????????? | | `true` `false` |
| `Recipe` | Current Recipe | | `` `null` |
| `S plus` | Is the grill running Smoke Plus? | | `true` `false` |  
| `Safety` | | `afterstarttemp` `reignitelaststate` `reigniteretries` `startuptemp` |  `Integer` |
| `Setpoints` | Change this to change set point | `grill` `grill_notify` `probe1` `probe2` |  `Integer` |
| `Settings update` | ???????? | |  `true` `false` |
| `Smartstart` | ??????? | `profile_selected` `startuptemp` |  `integer` |
| `Status` | ????????? | |  `null` |
| `Timer` | Grill's Timer | `end` `paused` `shutdown` `start` | | `Integer` |
| `Tuning mode` | ???????? | | `true` `false` |
| `Units change` | ????????? |  | `true` `false` |
| `Updated` | A check to see if mode has changed | | `true` `false` |
