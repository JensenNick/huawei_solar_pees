<a href='https://ko-fi.com/U7U1R0IQA' target='_blank'><img height='36' align='right' style='border:0px;height:36px;' src='https://storage.ko-fi.com/cdn/kofi2.png?v=3' border='0' alt='Buy Nick a Coffee at ko-fi.com' /></a>

# Huawei Solar - PEES

**Power, Energy and Economy Sensors**<br>

## Project Description

This project will provide you with a set of custom sensors to be used in HomeAssistant also refered to as the *"Huawei Solar PEES package"*. These custom sensors will calculate all the power and energy flows of your Huawei FusionSolar PV installation with Battery. On top of this the provided sensors will calculate expenses with and without solar PV and the Net Return of  Investment (NRI) - this will give you a fairly exact idea about the profitability of your investment in several aspects.

This README guides you through a simple setup process. For an overview and a more detailed description of the sensors included in the *"Huawei Solar PEES package"*, please refer to the [Wiki Pages](https://github.com/JensenNick/huawei_solar_pees/wiki). The experienced HomeAssistant user may find this guide banal - but this is to include all users, also the ones just starting out.

The provided custom sensors are based on a setup with two inverters and one battery. This is reflected throughout this README and the [Wiki Pages](https://github.com/JensenNick/huawei_solar_pees/wiki). The custom sensors are available as a package for an easy "installation". See more about this in chapter 3. Installation.

## Table of Content

1. [Before You Start](#1-before-you-start)
2. [Flow and Definitions](#2-flow-and-definitions)
3. [Installation](#3-installation)<br>
   3.1 [Package "Installation"](#31-package-installation)<br>
   3.2 [Input Sensors and Settings](#32-input-sensors-and-settings)<br>
   3.3 [Optional](#33-optional)<br>
4. [Known "bugs"](#4-known-bugs)
5. [Thanks to](#5-thanks-to)

## 1. Before You Start

The custom sensors in the *"Huawei Solar PEES package"* are all based on only three types of power sensors provided by the *"Huawei Solar integration by wlcrs"* - this makes the sensors robust and the margin for error is minimized. You also need a sensor to provide you with current electrical prices. I use the *"Energi Data Service integration by MTrab"*. These two custom integrations needs to be installed in HomeAssistant before you start. Both of the integrations can be installed via HACS.

- **Huawei Solar** integration by wlcrs <https://github.com/wlcrs/huawei_solar>
- **Energi Data Service** integration by MTrab (or similar integration to fetch the current electricity price incl. VAT and tariffs) <https://github.com/MTrab/energidataservice>

You also need an editor in HomeAssistant to be able to edit your configurations.yaml file. I use Studio Code Server (Visual Studio Code) as an Add-on in HomeAssistant.

Please note that the *"Huawei Solar PEES package"* is not an integration, it is a set of custom sensors I share. Please also note the number of custom sensors provided.

> :exclamation: **It is always good practise to create a full backup before you start!**

## 2. Flow and Definitions

The diagram below shows the definitions used for the power- and energy flows between the Solar PV, House, Battery, and Grid. These definitions are used in the naming convention of the custom sensors included in the *"Huawei Solar PEES package"*. The diagram is pretty straightforward but take a moment to study it to get acquainted with the definitions used.

![Definitions and Flows](pictures/flows_definitions.jpg)

## 3. Installation
The custom sensors included in the *"Huawei Solar PEES package"* are available for download as a single file, a "package", for easy copy/paste "installation". You can read more about packages in the HomeAssistant documentation about [Packages](<https://www.home-assistant.io/docs/configuration/packages/>).

### 3.1 Package "Installation"
The "install" is very straight forward and each step is described in the bulleted list below. Just for the overview - the proces includes configuring your configuration.yaml file, creating af directory/folder for the *"Huawei Solar PEES package file"* and copy/paste the package file into the directory/folder you have created. The package file also includes a short instruction.

* Open Studio Code Server (your code editor) and ad the following two lines to your `configuration.yaml` file.
```yaml
homeassistant:
  packages: !include_dir_named packages
```
* Create a directory/folder named `packages` in the `CONFIG` directory/folder (the main directory/folder).
* Copy the package file [huawei_solar_pees.yaml](packages/huawei_solar_pees.yaml) into your `packages` directory/folder.

### 3.2 Input Sensors and Settings
In order for the custon sensors to work properly you need to make sure that the naming of your input sensors is correct. As mentioned the custom sensor relly on three types of power sensors from the *"Huawei Solar integration by wlcrs"* and two electricity price sensors from the *"Energi Data Service integration by MTrab"*.

#### Power Sensors
The three types of input sensors from the *"Huawei Solar integration"* are `inverter_input_power`, `power_meter_active_power` and `battery_charge_discharge_power`. The naming use in the package file is corresponding to the default naming used in the *"Huawei Solar integration"* - so if you just stick with that you do not need to edit anything.
 
In the package file [huawei_solar_pees.yaml](packages/huawei_solar_pees.yaml) you will find the following text lines (not part of the code) which allows for an easy global edit if you need to edit the names of your power sensors.

```yaml
# - 'sensor.inverter_input_power' (from the Huawei Solar integration)
# - 'sensor.inverter_input_power_2' (from the Huawei Solar integration)
# - 'sensor.power_meter_active_power' (from the Huawei Solar integration)
# - 'sensor.battery_charge_discharge_power' (from the Huawei Solar integration)
 ```
If you have a single inverter setup, you can use the above method to delete all occurencies of the sensor `sensor.inverter_input_power_2` or, for a less troublesome edit when/if the package file may be revised, just set the state of `sensor.inverter_input_power_2 to be 0 (zero). Change the `state:` of the sensor `sensor.inverter_input_power_2`, 

From:
```yaml
      - name: "Power Inverter #2 Input"
        unique_id: power_inverter_2_input
        unit_of_measurement: W
        device_class: power
        state_class: measurement
        state: >
          {{ states('sensor.inverter_input_power_2') | float(0) }}
```
To:
```yaml
      - name: "Power Inverter #2 Input"
        unique_id: power_inverter_2_input
        unit_of_measurement: W
        device_class: power
        state_class: measurement
        state: 0
```

#### Electricity Price Sensors
You need to provide two electricity price sensors as input - one providing the price you pay pr. kWh for import/consumption and one providing the price pr. kWh that you receive for export/sale. The two sensors used in the *"Huawei Solar PEES package"* are from the *"Energi Data Service integration"* are `sensor.energi_data_service` and `sensor.energi_data_service_sale`. These are custom names that you can give the sensors when you add them as an entity with the integration.

As with the sensors above you will find the following lines in the package file [huawei_solar_pees.yaml](packages/huawei_solar_pees.yaml) for an easy global edit.

```yaml
# - 'sensor.energi_data_service' (price pr. kWh you pay for purchase/import)
# - 'sensor.energi_data_service_sale' (price pr. kWh you receive for sale/export)
```
If you use the *"Energi Data Service integration by MTrab"*, please refer to the [Wiki Pages](https://github.com/JensenNick/huawei_solar_pees/wiki/3.-Electricity-Tariffs-and-Price#energi-data-service-integration) for help with setting up the two electricity price sensors.

#### Currency
Last but not least you may need to correct the currency to your local currency. The currency used in the provided custom sensors is DKK (Danish Krone) and this is the price pr. kWh.

#### Restart
> :exclamation: **Thats it! Restart HomeAssistant and refresh your browser!**

> :bulb: Generally, it may take a little while before sensors register any activity/change and therefore will have the status "Unavailable" or "Unknown" initially - don't panic, be patient for the values to show.

### 3.3 Optional
#### Efficiency Corrected Inverter Power Input Sensor
The default custom sensor do not take the inverter efficiency into account which may result in a too high yield and other inaccuracies (house load is calculated on basis of the yield). The *"Huawei Solar integration"* does provide the `sensor.input_power_with_efficiency_loss` which takes the inverter efficiency into account. I have not tested this sensor, but my assessment is that it may cause inaccuracies and/or errors due to the step-by-step adjustment of the efficiency.

Therefore and as an alternative I have created two custom sensors - one for the Huawei SUN2000 3/4/5/6/8/10KTL-M1 (triple phase) inverters and one for the Huawei SUN2000 2/3/3.68/4/4.6/5/6KTL-L1 (single phase) inverters. The sensors are basically created as f(x) functions based on the efficiency graphs provided by Huawei in the data sheet.

Please refer to the [Wiki Pages](https://github.com/JensenNick/huawei_solar_pees/wiki/1.-Power-Sensors#efficiency-corrected-inverter-power-sensors) for an easy copy/paste of this efficiency corrected sensor. The Wiki Pages includes an overview and a short description of the parameters used in the Efficiency Corrected Inverter Power Input Sensor.

#### Tariffs
If you have several tariffs and/or it/they change from time to time, you might find it benificial to have a calculation of the settings you use. I have a sensor which was created for my *"Huawei Solar EFLR package"* but you might find it usefull in this case also. Please refer to the [Wiki Pages](https://github.com/JensenNick/huawei_solar_pees/wiki/3.-Electricity-Tariffs-and-Price#tariff-on-export-and-sale) where you will find an input redy to copy/paste.

## 4. Known "bugs"
None at the moment.

## 5. Thanks to
**A huge thanks to;**

- **wlcrs** for providing the *"Huawei Solar integration"*. This integration is essential for anyone who wishes to integrate their Huawei Solar PV in HomeAssistant.

- **MTrab** for providing the *"Energi Data Service integration"*. This integration is essential for all of us trying to keep up with the electricity prices and the complex and ever-changing tariffs in DK.

- **KennethLavrsen** for providing the full input for the triggered template sensors used to convert the Riemann Sum into actual economical figures.

**Again, Thank You to all of You!**
