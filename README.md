An addition to the Sungrow Inverter Repository from mkaiser.

# Contents
- [1. Overview](#1-overview)
- [2. Documentation](#2-documentation)
    - [Installation/ Configuration](#21-installation)
    - [Dashboard Setup](#22-dashboard-setup)
    - [Usage Instructions](#23-usage-instructions)
- [3. Support](#3-support)
- [4. Visual impressions](#4-visual-impressions)

# 1. Overview

This integration lets you gather sensor data and control several parameters of (currently only one) Sungrow Wallbox, the AC011E-01.

Please ensure the connection to either the inverter or other connection to a network is stable, else you might get false readings.

## 2. Documentation

The documentation covers following topics:

### 2.1. Installation
#### 2.1.1. Lookup slave id of wallbox
Open the WiNet-S web interface /LAN or WLAN) and lookup the slave id of your wallbox (here 3):
![image](https://github.com/SunnyCrockett/Sungrow-Wallbox-Modbus-HomeAssistant/assets/153714968/fe607ab4-1f6f-4ffc-b2cd-eac9775efe32)

#### 2.1.2. secrets.yaml
Add the following lines to your secrets.yaml and set your values:
```
wallbox_modbus_host_ip: expressif  # TODO update with the IP of your inverters WiNet-S dongle (not ModBus LAN port). No default. Check your router.
wallbox_modbus_port: 502 # TODO update with the Modbus port of your inverter WiNet-S dongle. Default is '502'
wallbox_modbus_slave: 3 #TODO update with the slave address of your wallbox. Default is '3'
```
#### 2.1.3. Home Assistant configuration

The file modbus_wallbox.yaml contains the Modbus register maps, template sensors and automations. Copy the file to a subfolder named "integrations" (maybe create it first), which is located at the same level as your "configurations.yaml".

Include "modbus_wallbox.yaml" by adding the follwing lines to your "configuration.yaml":
```
homeassistant:
  packages: !include_dir_named integrations
```
Do not forget to check your configuration (Developer Tools --> hit "check configuration" and restart: it won't work without a restart!)

After the restart, some new sensors should be available. E.g., check for "Wallbox device type"

### 2.2. Dashboard setup
[Dashboard Setup](https://github.com/Louisbertelsmann/Sungrow-Wallbox-Modbus-HomeAssistant/wiki/Dashboard-Setup)

### 2.3. Usage instructions
[Usage Instructions](https://github.com/Louisbertelsmann/Sungrow-Wallbox-Modbus-HomeAssistant/wiki/Usage-instructions)

## 3. Support

If you any kind of assistance, you have two options:

- Use the [github discussion](../../discussions) 

- Only if code-related (bugs / contributions): Open an  [github issue](../../issue) or isse a pullrequest

## 4. Visual impressions
![infos](https://github.com/SunnyCrockett/Sungrow-Wallbox-Modbus-HomeAssistant/assets/153714968/df966f51-7655-40e3-bc35-ef90e99655e4)
![last](https://github.com/SunnyCrockett/Sungrow-Wallbox-Modbus-HomeAssistant/assets/153714968/645b4521-c40f-420e-a364-19488f2b672f)
![current](https://github.com/SunnyCrockett/Sungrow-Wallbox-Modbus-HomeAssistant/assets/153714968/1bf2b6fc-6277-4886-beb2-96e014d72531)
![settings](https://github.com/SunnyCrockett/Sungrow-Wallbox-Modbus-HomeAssistant/assets/153714968/86569e0f-428e-4da5-9035-13cc9f2628f5)
