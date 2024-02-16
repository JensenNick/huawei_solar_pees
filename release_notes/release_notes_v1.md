# Huawei Solar - PEES

**Power, Energy and Economy Sensors**

## Release Note / v1.0.0

The *"Huawei Solar PEES package file"* has now been tested on a clean install of Home Assistant - no strings to any thing in the past. This is hopefully how most of you will experience the "installation".

### New naming convention

This wasn't an easy decision, but for the better I believe looking forward. Template sensors lose their value temporarily while HA is rebooting / restarting, leaving a blank space in the graphs. I therefor upgraded the *"Huawei Solar PEES package"* with utility meters for all the platform and template sensors.

I could have gone with a new suffix some of the utility meters, but that would have been inconsistent and an annoyance when these utility meters would be used in cards, energy dashboard etc. - you would have had to change the name of the source every time you use it. So, I have decided to re-name the platform sensors, template sensors and template trigger sensors respectively with the suffix as follows,

* `_ps` for platform sensor,
* `_ts` for template sensor and
* `_tt` for template trigger sensor.

There are other bonus effects to this as well, 1) utility meters are easier to reset and calibrate without the need for a deep dive into your database 2) you can now easily identify the origin of the sensor and 3) easy filtering based on the new suffix.

### Error in code

A crucial error in the attribute for the sensor `battery_charge_yield_sale` has been corrected (new sensor name `battery_charge_yield_sale_tt`),

### PV template sensors

The device_class on the PV sensors has been removed, in order to allow state_ class: total_increasing. Forum posts from the Developers suggest not to use device_class for this type of sensors.

### Dashboards

Codes for input to the dashboards have been updated so they match the new naming convention.

### Info

Version number, domain name and code owner has been added to the `huawei_solar_pees.yaml` package file

### Documentation

Has not yet been updated accordingly to above changes.
