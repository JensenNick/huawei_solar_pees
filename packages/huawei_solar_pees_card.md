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
      - entity: input_text.electricity_price_import
      - entity: input_text.electricity_price_export
    title: Electricity Price
  - type: entities
    entities:
      - entity: input_text.currency
    title: Currency