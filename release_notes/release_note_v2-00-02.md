# Huawei Solar - PEES

**Power, Energy and Economy Sensors**

## Release Note / v2.0.1 and v2.0.2

Minor changes to Energy Yield Total (ts)

## Release Note / v2.0.0

The *"Huawei Solar PEES package file"* has been upgraded to version 2.0.0 and with this leap comes interaction via the GUI the ability to save most of your user specific settings and the possibility to the efficiency corrected power input sensor without the need for any copy/pasting.

### The package

The *"Huawei Solar PEES package"* now includes 3 files - 1) the `huawei_solar_pees.yaml` file that contain all the custom sensors included in the *"Huawei Solar PEES package"*, 2) the `huawei_solar_input.yaml` file that contain sensors for your user specific solar PV settings, and 3) the `huawei_solar_input_card.md` file that contains the code for the Lovelace card / GUI interface.

> :bulb: The *"Huawei Solar PEES package"* will work "out of the box". You do not have to use/setup the user specific settings and the Lovelace card. But you have to copy both `yaml` files into you package folder/directory for the custom sensors to work.

### Efficiency Corrected Input Power

Previusly you had to copy/paste the efficiency corrected input power sensor input the `huawei_solar_pees.yaml` file and delete the default power sensor. The efficiency corrected input power sensor is now "activated" via the two boolean switches on the Lovelace card, where you also choose the number of phases your inverter has.

From here you  will now be presented with a drop down menu where you choose your specific inverter model.

Below the drop down menu with the inverter models you wil have two sliders, one to control the operating voltage and one to control the overall factor. The README explain what these slides do / how they effect the power input.

> :bulb: If you do not want the efficiency corrected sensor you just leave the two boolean switches off.

### Electricity Price Sensor

The Lovelace card also includes a text box, where it is now possible to add your choice of electricity price sensors. Just ad the sensor name and the calculations will be based on your specific electricity price sensor. The folowing sensors have been added.

* `sensor.electricity_price_import_ts`
* `sensor.electricity_price_export_ts`

<br>

> :bulb: The electricity price sensors (with sensor names according to the README) from the *"Energi Data Service integration"* are used as default sensors.

### New Economy Sensors

To address [issue #29](https://github.com/JensenNick/huawei_solar_pees/issues/29) with the late start up of some of the economy sensors, it has been necessary to add a few template sensors in order to set an availibility on them individualy. To my knowledge it is a bit unorthodox to create a template sensor based on a utility meter, but none the less it solves the issue. The new template sensors are,

* `sensor.battery_charge_yield_sale_ts`
* `sensor.battery_charge_grid_cost_ts`
* `sensor.battery_discharge_grid_sale_ts`
* `sensor.battery_discharge_house_saving_ts`

### New Energy Sensoors

In the same manner the same principal sollution has been used to improve setup procedure for those with a single inverter setup. Sensor `sensor.energy_yield_total_ts` will now be active without the need to manually set `sensor.energy_yield_2_ts` to 0 (zero). The new template sensors are,

* `sensor.energy_yield_1_ts`
* `sensor.energy_yield_2_ts`

### Unique ID on All Utility Meters

All utility meters have now been provided with a `unique_id` which alow you to edit the precision and the icon in the GUI.

### Documentation

The README is up to date with the latest changes. The Wiki Pages are under revision due to these changes.
