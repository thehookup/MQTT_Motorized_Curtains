# MQTT_Motorized_Curtains
Stepper motor controlled MQTT curtains - Home Assistant Integrated

## Initial Setup

1. Download the .ino file
2. Ensure you have the correct libraries download and installed (links at top of the ino file)
3. Update information in the user configuration section and upload to the NodeMCU
4. Hook up your NodeMCU, stepper driver and motor as shown in the wiring section
5. Send a value of 0 to the position MQTT topic which will be:

```c++
[USER_MQTT_CLIENT_NAME]/positionCommand
```
6. Send incrementally higher values to the position MQTT topic until your blinds are fully closed
7. Input that position value into the STEPS_TO_CLOSE field in the arduino sketch.
8. Send the updated file to your NodeMCU.


## Parts (Amazon Links)

Stepper Package 	        https://amzn.to/2MpRQPu


Pulleys	 	                https://amzn.to/2FLbCDI


Curtain Rope		          https://amzn.to/2U7h5Zs


Extruder Gear	 	          https://amzn.to/2T4QtrL


Bearings		              https://amzn.to/2U4bdQI


NodeMCU	                	https://amzn.to/2MkBcka


Buck Converter	 	        https://amzn.to/2FEcNFF


Power Supply		          https://amzn.to/2MmtFBj


M3 x 20mm	       	        Home Depot


#10 bolt	       	        Home Depot


## Wiring

![alt text](https://github.com/thehookup/MQTT_Motorized_Curtains/blob/master/schematic.jpg)

## Stepper Dip Switch Positions

![alt text](https://github.com/thehookup/MQTT_Motorized_Curtains/blob/master/dip_switches.jpg)

## Motor Hardware Setup

![alt text](https://github.com/thehookup/MQTT_Motorized_Curtains/blob/master/Motor_Setup_Image.jpg)

## Home Assistant YAML

```yaml
cover:
  - platform: mqtt
    name: "Downstairs Curtains"
    command_topic: "CurtainsMCU/command"
    set_position_topic: "CurtainsMCU/positionCommand"
    position_topic: "CurtainsMCU/positionState"
    state_topic: "CurtainsMCU/positionState"
    retain: true
    payload_open: "OPEN"
    payload_close: "CLOSE"
    payload_stop: "STOP"
    position_open: 88
    position_closed: 0
```

