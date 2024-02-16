# Huawei Solar - PEES

**Power, Energy and Economy Sensors**

## Release Note / v2.0.5

### Issue

Issue with utility meter jumping at restart and reboot fixed. This issue especially conserns the economy utility meters. The fix includes rolling back the new sensors introduced in v2.0.0.

### Sensors Removed

The following sensors introdiced in version v2.0.0 are being removed as they were intended to solve the issue described above.

* `sensor.battery_charge_yield_sale_ts`
* `sensor.battery_charge_grid_cost_ts`
* `sensor.battery_discharge_grid_sale_ts`
* `sensor.battery_discharge_house_saving_ts`

### Documentation

The README is up to date with the latest changes. The Wiki Pages are under revision due to these changes.