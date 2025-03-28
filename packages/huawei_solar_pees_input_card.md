## Huawei Solar PEES INPUT CARD
version: <br>
branch: alpha-028<br>
domain: https://github.com/JensenNick/huawei_solar_pees<br>
codeowner: Nick Jensen<br>

### Input Card for the *"Huawei Solar PEES package"*

```yaml
type: vertical-stack
cards:
  - type: entities
    entities:
      - entity: input_boolean.pees_efficiency_corrected_power_input
      - entity: input_boolean.pees_include_ev_charger
    title: Enable / Disable PEES Functions
    show_header_toggle: false
  - type: entities
    entities:
      - entity: sensor.pees_inverter_1_model
    title: "Inverter #1"
  - type: conditional
    conditions:
      - condition: state
        entity: input_boolean.pees_efficiency_corrected_power_input
        state: "on"
    card:
      type: vertical-stack
      cards:
        - type: conditional
          conditions:
            - condition: state
              entity: binary_sensor.pees_inverter_1_is_l1
              state: "on"
          card:
            type: entities
            entities:
              - entity: input_number.pees_inverter_1_operating_voltage_l1
              - entity: input_number.pees_inverter_1_overall_factor
        - type: conditional
          conditions:
            - condition: state
              entity: binary_sensor.pees_inverter_1_is_lc0
              state: "on"
          card:
            type: entities
            entities:
              - entity: input_number.pees_inverter_1_operating_voltage_lc0
              - entity: input_number.pees_inverter_1_overall_factor
        - type: conditional
          conditions:
            - condition: state
              entity: binary_sensor.pees_inverter_1_is_m1
              state: "on"
          card:
            type: entities
            entities:
              - entity: input_number.pees_inverter_1_operating_voltage_m1
              - entity: input_number.pees_inverter_1_overall_factor
        - type: conditional
          conditions:
            - condition: state
              entity: binary_sensor.pees_inverter_1_is_map0
              state: "on"
          card:
            type: entities
            entities:
              - entity: input_number.pees_inverter_1_operating_voltage_map0
              - entity: input_number.pees_inverter_1_overall_factor
        - type: conditional
          conditions:
            - condition: state
              entity: binary_sensor.pees_inverter_1_is_mb0
              state: "on"
          card:
            type: entities
            entities:
              - entity: input_number.pees_inverter_1_operating_voltage_mb0
              - entity: input_number.pees_inverter_1_overall_factor
        - type: entities
          entities:
            - entity: sensor.inverter_pv_1_voltage
            - entity: sensor.inverter_pv_2_voltage
  - type: entities
    entities:
      - entity: sensor.pees_inverter_2_model
    title: "Inverter #2"
  - type: conditional
    conditions:
      - condition: state
        entity: input_boolean.pees_efficiency_corrected_power_input
        state: "on"
    card:
      type: vertical-stack
      cards:
        - type: conditional
          conditions:
            - condition: state
              entity: binary_sensor.pees_inverter_2_is_l1
              state: "on"
          card:
            type: entities
            entities:
              - entity: input_number.pees_inverter_2_operating_voltage_l1
              - entity: input_number.pees_inverter_2_overall_factor
        - type: conditional
          conditions:
            - condition: state
              entity: binary_sensor.pees_inverter_2_is_lc0
              state: "on"
          card:
            type: entities
            entities:
              - entity: input_number.pees_inverter_2_operating_voltage_lc0
              - entity: input_number.pees_inverter_2_overall_factor
        - type: conditional
          conditions:
            - condition: state
              entity: binary_sensor.pees_inverter_2_is_m1
              state: "on"
          card:
            type: entities
            entities:
              - entity: input_number.pees_inverter_2_operating_voltage_m1
              - entity: input_number.pees_inverter_2_overall_factor
        - type: conditional
          conditions:
            - condition: state
              entity: binary_sensor.pees_inverter_2_is_map0
              state: "on"
          card:
            type: entities
            entities:
              - entity: input_number.pees_inverter_2_operating_voltage_map0
              - entity: input_number.pees_inverter_2_overall_factor
        - type: conditional
          conditions:
            - condition: state
              entity: binary_sensor.pees_inverter_2_is_mb0
              state: "on"
          card:
            type: entities
            entities:
              - entity: input_number.pees_inverter_2_operating_voltage_mb0
              - entity: input_number.pees_inverter_2_overall_factor
        - type: entities
          entities:
            - entity: sensor.inverter_pv_1_voltage_2
            - entity: sensor.inverter_pv_2_voltage_2
  - type: entities
    entities:
      - entity: input_text.pees_electricity_price_import
      - entity: input_text.pees_electricity_price_export
      - entity: input_text.pees_electricity_price_ev_charging
    title: Electricity Price
  - type: conditional
    conditions:
      - condition: state
        entity: input_boolean.pees_include_ev_charger
        state: "on"
    card:
      type: entities
      entities:
        - entity: input_text.pees_power_ev_charger
      title: EV Charger
```

### Power Sensors Card for the *"Huawei Solar PEES package"*

```yaml
square: false
type: grid
cards:
  - type: vertical-stack
    cards:
      - type: entities
        entities:
          - entity: sensor.pees_power_inverter_input_total
            icon: mdi:solar-power-variant-outline
          - entity: sensor.power_meter_active_power
            icon: mdi:counter
          - entity: sensor.batteries_charge_discharge_power
            icon: mdi:home-battery-outline
        title: Power
      - type: entities
        entities:
          - entity: sensor.pees_power_inverter_input_total
            icon: mdi:solar-power-variant-outline
          - entity: sensor.pees_power_inverter_1_input
            icon: mdi:solar-power-variant-outline
          - entity: sensor.pees_power_inverter_2_input
            icon: mdi:solar-power-variant-outline
        title: "- Yield"
      - type: entities
        entities:
          - entity: sensor.power_meter_active_power
            icon: mdi:counter
          - entity: sensor.pees_power_export
            icon: mdi:home-export-outline
          - entity: sensor.pees_power_import
            icon: mdi:home-import-outline
          - entity: sensor.pees_power_export_yield
            icon: mdi:solar-power-variant-outline
          - entity: sensor.pees_power_battery_discharge_grid
            icon: mdi:home-battery-outline
        title: "- Import / Export"
      - type: entities
        entities:
          - entity: sensor.pees_power_house_load
            icon: mdi:home-lightning-bolt-outline
          - entity: sensor.pees_power_house_load_yield
            icon: mdi:solar-power-variant-outline
          - entity: sensor.pees_power_house_load_grid
            icon: mdi:home-import-outline
          - entity: sensor.pees_power_battery_discharge_house
            icon: mdi:home-battery-outline
        title: "- House Load"
      - type: entities
        entities:
          - entity: sensor.batteries_charge_discharge_power
            icon: mdi:home-battery-outline
          - entity: sensor.pees_power_battery_charge
            icon: mdi:battery-charging-low
          - entity: sensor.pees_power_battery_discharge
            icon: mdi:battery-charging-high
          - entity: sensor.pees_power_battery_charge_grid
            icon: mdi:battery-charging-low
          - entity: sensor.pees_power_battery_charge_yield
            icon: mdi:battery-charging-medium
          - entity: sensor.pees_power_battery_discharge_grid
            icon: mdi:battery-charging-high
          - entity: sensor.pees_power_battery_discharge_house
            icon: mdi:battery-charging-high
        title: "- Battery Charge / Discharge"
columns: 1
```

### Energy Sensors Card for the *"Huawei Solar PEES package"*

```yaml
square: false
type: grid
cards:
  - type: vertical-stack
    cards:
      - type: entities
        title: Energy
        entities:
          - entity: sensor.pees_total_energy_yield_total
            icon: mdi:solar-power-variant-outline
          - entity: sensor.pees_total_energy_import
            icon: mdi:home-import-outline
          - entity: sensor.pees_total_energy_export_yield
            icon: mdi:home-export-outline
      - type: entities
        title: "- Yield"
        entities:
          - entity: sensor.pees_total_energy_yield_total
            icon: mdi:solar-power-variant-outline
          - entity: sensor.pees_total_energy_yield_1
            icon: mdi:solar-power-variant-outline
          - entity: sensor.pees_total_energy_yield_2
            icon: mdi:solar-power-variant-outline
      - type: entities
        title: "- House"
        entities:
          - entity: sensor.pees_total_energy_house_load
            icon: mdi:home-lightning-bolt-outline
          - entity: sensor.pees_total_energy_house_load_grid
            icon: mdi:home-import-outline
          - entity: sensor.pees_total_energy_house_load_yield
            icon: mdi:solar-power-variant-outline
          - entity: sensor.pees_total_energy_battery_discharge_house
            icon: mdi:home-battery-outline
      - type: entities
        title: "- Battery"
        entities:
          - entity: sensor.pees_total_energy_battery_charge
            icon: mdi:battery-charging-low
          - entity: sensor.pees_total_energy_battery_discharge
            icon: mdi:battery-charging-high
          - entity: sensor.pees_total_energy_battery_charge_grid
            icon: mdi:battery-charging-low
          - entity: sensor.pees_total_energy_battery_charge_yield
            icon: mdi:battery-charging-medium
          - entity: sensor.pees_total_energy_battery_discharge_grid
            icon: mdi:battery-charging-high
          - entity: sensor.pees_total_energy_battery_discharge_house
            icon: mdi:battery-charging-high
columns: 1
```

### Yield and Consumption Card for the *"Huawei Solar PEES package"*

```yaml
square: false
type: grid
cards:
  - type: entities
    entities:
      - entity: sensor.pees_total_energy_yield_total
        type: custom:multiple-entity-row
        icon: mdi:solar-power-variant-outline
        name: Yield
        state_header: Total
        secondary_info: false
        format: precision2
        entities:
          - entity: sensor.pees_total_energy_house_load_yield
            name: House
            format: precision2
          - entity: sensor.pees_total_energy_battery_charge_yield
            name: Battery
            format: precision2
          - entity: sensor.pees_total_energy_export
            name: Export
            format: precision2
      - entity: sensor.pees_total_energy_house_load
        type: custom:multiple-entity-row
        icon: mdi:home-lightning-bolt-outline
        name: Consumption
        state_header: Total
        secondary_info: false
        format: precision2
        entities:
          - entity: sensor.pees_total_energy_house_load_yield
            name: Yield
            format: precision2
          - entity: sensor.pees_total_energy_battery_discharge_house
            name: Battery
            format: precision2
          - entity: sensor.pees_total_energy_house_load_grid
            name: Import
            format: precision2
    state_color: true
    title: Yield & Consumption
  - type: entities
    entities:
      - entity: sensor.pees_total_energy_battery_charge
        type: custom:multiple-entity-row
        icon: mdi:battery-charging-medium
        name: Battery
        state_header: Charge
        secondary_info: false
        format: precision2
        entities:
          - entity: sensor.pees_total_energy_battery_discharge
            name: Discharge
            format: precision2
          - entity: sensor.pees_total_energy_battery_charge_yield
            name: Yield
            format: precision2
          - entity: sensor.pees_total_energy_battery_charge_grid
            name: Import
            format: precision2
    state_color: true
  - type: entities
    entities:
      - entity: sensor.pees_economy_result_w_pv
        type: custom:multiple-entity-row
        name: Economy w PV
        secondary_info: false
        state_header: Cost w PV
        format: precision2
        entities:
          - entity: sensor.pees_economy_expenses_w_pv
            name: Import
            format: precision2
          - entity: sensor.pees_economy_income_w_pv
            name: Export
            format: precision2
      - entity: sensor.pees_economy_result_wo_pv
        type: custom:multiple-entity-row
        name: Economy wo PV
        secondary_info: false
        state_header: Cost wo PV
        format: precision2
        entities:
          - entity: sensor.pees_total_energy_house_load
            name: Consumption
            format: precision2
      - entity: sensor.pees_total_economy_nri_pv
        type: custom:multiple-entity-row
        name: Net Return
        secondary_info: false
        state_header: NRI Total
        format: precision2
        entities:
          - entity: sensor.pees_total_economy_nri_battery
            name: NRI Battery
            format: precision2
    state_color: true
columns: 1
```

### Net Return on Investment Card for the *"Huawei Solar PEES package"*

```yaml
square: false
type: grid
cards:
  - type: entities
    entities:
      - entity: sensor.pees_economy_nri_pv
      - entity: sensor.pees_economy_nri_battery
    title: Net Return of Investment
  - type: entities
    entities:
      - entity: sensor.pees_economy_expenses_w_pv
      - entity: sensor.pees_economy_income_w_pv
      - entity: sensor.pees_economy_result_w_pv
      - entity: sensor.pees_economy_result_wo_pv
    title: Expenses & Income
columns: 1
```
