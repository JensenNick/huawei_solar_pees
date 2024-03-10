## Huawei Solar INPUT CARD - Input Card for Lovelace
version: v1.0.2<br>
branch: main<br>
domain: https://github.com/JensenNick/huawei_solar_pees<br>
codeowner: Nick Jensen<br>

### Input Card for the *"Huawei Solar PEES package"*

```yaml
type: vertical-stack
cards:
  - type: entities
    entities:
      - entity: input_boolean.inverter_1_1phase
        name: 'Inverter #1 SUN2000 # KTL-L1 (1 phase)'
      - entity: input_boolean.inverter_1_3phase
        name: 'Inverter #1 SUN2000 # KTL-M1 (3 phase)'
    title: 'Inverter #1'
    show_header_toggle: false
  - type: conditional
    conditions:
      - condition: state
        entity: input_boolean.inverter_1_1phase
        state: 'on'
      - condition: state
        entity: input_boolean.inverter_1_3phase
        state: 'off'
    card:
      type: entities
      entities:
        - entity: input_select.inverter_1_1phase_models
        - entity: input_number.inverter_1_operating_voltage_l1
          name: Operating voltage (360V)
        - entity: input_number.inverter_1_overall_factor
          name: Overall factor (100%)
  - type: conditional
    conditions:
      - condition: state
        entity: input_boolean.inverter_1_3phase
        state: 'on'
      - condition: state
        entity: input_boolean.inverter_1_1phase
        state: 'off'
    card:
      type: entities
      entities:
        - entity: input_select.inverter_1_3phase_models
        - entity: input_number.inverter_1_operating_voltage_m1
          name: Operating voltage (600V)
        - entity: input_number.inverter_1_overall_factor
          name: Overall factor (100%)
  - type: entities
    entities:
      - entity: sensor.inverter_pv_1_voltage
      - entity: sensor.inverter_pv_2_voltage
  - type: entities
    entities:
      - entity: input_boolean.inverter_2_1phase
        name: 'Inverter #2 SUN2000 # KTL-L1 (1 phase)'
      - entity: input_boolean.inverter_2_3phase
        name: 'Inverter #2 SUN2000 # KTL-M1 (3 phase)'
    title: 'Inverter #2'
    show_header_toggle: false
  - type: conditional
    conditions:
      - condition: state
        entity: input_boolean.inverter_2_1phase
        state: 'on'
      - condition: state
        entity: input_boolean.inverter_2_3phase
        state: 'off'
    card:
      type: entities
      entities:
        - entity: input_select.inverter_2_1phase_models
        - entity: input_number.inverter_2_operating_voltage_l1
          name: Operating voltage (360V)
        - entity: input_number.inverter_2_overall_factor
          name: Overall factor (100%)
  - type: conditional
    conditions:
      - condition: state
        entity: input_boolean.inverter_2_3phase
        state: 'on'
      - condition: state
        entity: input_boolean.inverter_2_1phase
        state: 'off'
    card:
      type: entities
      entities:
        - entity: input_select.inverter_2_3phase_models
        - entity: input_number.inverter_2_operating_voltage_m1
          name: Operating voltage (600V)
        - entity: input_number.inverter_2_overall_factor
          name: Overall factor (100%)
  - type: entities
    entities:
      - entity: sensor.inverter_pv_1_voltage_2
      - entity: sensor.inverter_pv_2_voltage_2
  - type: entities
    entities:
      - entity: input_text.electricity_price_import
      - entity: input_text.electricity_price_export
    title: Electricity Price
```
### Input Card for the *"Huawei Solar STAT package"*

```yaml
type: vertical-stack
cards:
  - type: entities
    entities:
      - entity: input_number.battery_rated_capacity
        name: Rated Capacity (kWh)
      - entity: input_number.battery_efficiency_soc_trigger
        name: SOC Trigger (50%)
      - entity: input_number.battery_efficiency_start_value_charge
        name: Start Value Charge (kWh)
      - entity: input_number.battery_efficiency_start_value_discharge
        name: Start Value Discharge (kWh)
    title: Battery Efficiency
  - type: entities
    entities:
      - entity: input_number.panels_rated_wp
        name: Solar Panels Power (Wp)
      - entity: input_number.panels_on_inverter_1
        name: "Panels on inverter #1"
      - entity: input_number.panels_on_inverter_2
        name: "Panels on inverter #2"
    title: Yield Statistics
``` 
