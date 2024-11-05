# Huawei Solar - PEES

**Power, Energy and Economy Sensors**

## Release Note / v3.0.0

The *"Huawei Solar PEES package file"* has been upgraded to version v3.0.0 which apart from a new namining pricipal also now includes sensors relevant to monitor your EV.

> :exclamation: **This revision is NOT backwards compatibile** :exclamation:

About the new naming principal:

* All sensors / enteties have been renamed with the prefix "pees". This is in order to follow "propper" naming pricipals. It will make it much esier to identify and isolate the sensors / enteties related to the package.

* Utility Meters wo a cycle has been given the prefix "total" wich allows the utility meter to follow the naming principal used for the input sensor.

* The above change has made the somewhat unorthodox sufix "_ps", "_ts" and "_tt" obsolete.

The `sensor.tariff_export` and `energi_data_service_negative` have been deleted from the Input file, since they do not have a direct relation to the package. The sensors are still available in the [Wiki Pages](https://github.com/JensenNick/huawei_solar_pees/wiki/4.-Electricity-Tariffs-and-Price#extras).
