## Huawei Solar STAT INPUT CARD - Input Card for Lovelace
version: v1.0.0<br>
branch: main<br>
domain: https://github.com/JensenNick/huawei_solar_stat<br>
codeowner: Nick Jensen<br>

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
