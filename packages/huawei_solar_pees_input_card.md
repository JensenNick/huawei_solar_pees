## Huawei Solar PEES INPUT CARD - Input Card for Lovelace
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
            - entity: sensor.pees_inverter_pv_1_voltage
            - entity: sensor.pees_inverter_pv_2_voltage
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
            - entity: sensor.pees_inverter_pv_1_voltage_2
            - entity: sensor.pees_inverter_pv_2_voltage_2
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