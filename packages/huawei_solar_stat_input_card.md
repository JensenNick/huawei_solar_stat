## Huawei Solar STAT INPUT CARD - Input Card for Lovelace
version: <br>
branch: alpha-001<br>
domain: https://github.com/JensenNick/huawei_solar_stat<br>
codeowner: Nick Jensen<br>

### Input Card for the *"Huawei Solar STAT package"*

```yaml
type: vertical-stack
cards:
  - type: entities
    entities:
      - entity: input_select.battery_model
    title: 'Battery Model and Data'
    show_header_toggle: false
  - type: conditional
    conditions:
      - condition: state
        entity: input_select.battery_model
        state: 'LUNA2000 S0'
    card:
      type: entities
      entities:
        - entity: input_number.battery_rated_capacity_s0
        - entity: input_number.battery_charge_power_s0
  - type: conditional
    conditions:
      - condition: state
        entity: input_select.battery_model
        state: 'LUNA2000 S1'
    card:
      type: entities
      entities:
        - entity: input_number.battery_rated_capacity_s1
        - entity: input_number.battery_charge_power_s1
  - type: entities
    entities:
      - entity: input_number.battery_efficiency_soc_trigger
        name: SOC Trigger (50%)
      - entity: input_number.battery_efficiency_start_value_charge
        name: Start Value Charge (kWh)
      - entity: input_number.battery_efficiency_start_value_discharge
        name: Start Value Discharge (kWh)
    title: Battery Efficiency Calculation
  - type: entities
    entities:
      - entity: input_number.panels_rated_wp
        name: Solar Panels Power (Wp)
      - entity: input_number.panels_on_inverter_1
        name: "Panels on inverter #1"
      - entity: input_number.panels_on_inverter_2
        name: "Panels on inverter #2"
    title: Input Solar Panels
```