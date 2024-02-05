<a href='https://ko-fi.com/U7U1R0IQA' target='_blank'><img height='36' align='right' style='border:0px;height:36px;' src='https://storage.ko-fi.com/cdn/kofi2.png?v=3' border='0' alt='Buy Nick a Coffee at ko-fi.com' /></a>

# Huawei Solar - STAT

**Energy Statistics Sensors**<br>

## Project Description
> :exclamation: **This project is under development** :exclamation:

This project will provide you with a set of custom sensors to be used in Home Assistant also refered to as the "Huawei Solar STAT package". These custom sensors will calculate energy statistics of your Huawei Solar PV system.

## Table of Content

## 1. Before You Start
The custom sensors in the *"Huawei Solar STAT package"* are based on sensors provided by the "Huawei Solar PEES package", which needs to be "installed" in Home Assistant before you start. Here is the link to my *"Huawei Solar PEES package"* and the latest release.

## 2. Sensors

### Self Sufficiency

| Name | Description |
| -- | -- |
| Energy Self Sufficiency (ts)<br> `energy_self_sufficiency_ts` | -<br> Attributes calculated selfsufficience daily, weekly, monthly, quarterly and yearly. |

### Yield pr. kWp

| Name | Description |
| -- | -- |
| Energy Yield Total pr kWp (ts)<br> `energy_yield_total_pr_kwp_ts` | - |
| Energy Yield #1 pr kWp (ts)<br> `energy_yield_1_pr_kwp_ts` | - |
| Energy Yield #2 pr kWp (ts)<br> `energy_yield_2_pr_kwp_ts` | - |

The package includes hourly, daily, weekly, monthly, quarterly and yearly utility meters to track "Yield pr. kWp"

### Price pr. kWh

| Name | Description |
| -- | -- |
| Price/kWh wo PV (ts)<br> `price_kwh_wo_pv_ts` | -<br> Attributes include daily, weekly, monthly, quarterly and yearly. |
| Price/kWh w PV (ts)<br> `price_kwh_w_pv_ts` | -<br> Attributes include daily, weekly, monthly, quarterly and yearly. |
| Price/kWh Export (ts)<br> `price_kwh_export_ts` | -<br> Attributes include daily, weekly, monthly, quarterly and yearly. |
| Price/kWh Export Yield (ts)<br> `price_kwh_export_yield_ts` | -<br> Attributes include daily, weekly, monthly, quarterly and yearly. |
| Price/kWh Export Battery Discharge (ts)<br> `price_kwh_export_battery_discharge_ts` | -<br> Attributes include daily, weekly, monthly, quarterly and yearly. |

### Battery Statistics

| Name | Description |
| -- | -- |
| Energy Battery Discharge Capacity (ts)<br> `energy_battery_Discharge_capacity_ts` | Available capacity for discharge, with your current settings |
| Enegy Battery Charge Grid Capacity (ts)<br> `energy_battery_charge_grid_capacity_ts` | Available space on your battery for charging over AC. *This could come in handy for charging automations* |
| Enegy Battery Charge Yield Capacity (ts)<br> `energy_battery_charge_yield_capacity_ts` | Available space on your battery for charging yield from your solar PV. *This could come in handy for charging automations* |
| Battery Efficiency Total (tt)<br> `battery_efficiency_total_tt` | The "total" efficiency of your battery, meaning from start of measuring until "now". |
