## Huawei Solar PEES INPUT CARD - Input Card for Lovelace
version: v1.0.3<br>
branch: main<br>
domain: https://github.com/JensenNick/huawei_solar_pees<br>
codeowner: Nick Jensen<br>

### Input Card for the *"Huawei Solar PEES package"*

```yaml
type: vertical-stack
cards:
  - type: entities
    entities:
      - entity: sensor.inverter_1_model
  - type: conditional
    conditions:
      - condition: state
        entity: binary_sensor.inverter_1_is_l1
        state: "on"
    card:
      type: entities
      entities:
        - entity: input_number.inverter_1_operating_voltage_l1
          name: Operating voltage (360V)
        - entity: input_number.inverter_1_overall_factor
          name: Overall factor (100%)
  - type: conditional
    conditions:
      - condition: state
        entity: binary_sensor.inverter_1_is_m1
        state: "on"
    card:
      type: entities
      entities:
        - entity: input_number.inverter_1_operating_voltage_m1
          name: Operating voltage (600V)
        - entity: input_number.inverter_1_overall_factor
          name: Overall factor (100%)
  - type: entities
    entities:
      - entity: sensor.inverter_pv_1_voltage
      - entity: sensor.inverter_pv_2_voltage
  - type: conditional
    conditions:
      - condition: state
        entity: binary_sensor.inverter_2_is_l1
        state: "on"
    card:
      type: entities
      entities:
        - entity: input_number.inverter_2_operating_voltage_l1
          name: Operating voltage (360V)
        - entity: input_number.inverter_2_overall_factor
          name: Overall factor (100%)
  - type: entities
    entities:
      - entity: sensor.inverter_2_model
  - type: conditional
    conditions:
      - condition: state
        entity: binary_sensor.inverter_2_is_m1
        state: "on"
    card:
      type: entities
      entities:
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