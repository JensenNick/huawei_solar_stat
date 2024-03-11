# Huawei Solar - STAT <a href='https://ko-fi.com/U7U1R0IQA' target='_blank'><img height='36' align='right' style='border:0px;height:36px;' src='https://storage.ko-fi.com/cdn/kofi2.png?v=3' border='0' alt='Buy Nick a Coffee at ko-fi.com' /></a>

**Energy and Price Statistics Sensors**<br>

## Project Description

This project will provide you with a set of custom sensors also referred to as the *"Huawei Solar STAT package"* to be used in Home Assistant . These custom sensors will calculate energy and price statistics of your Huawei Solar PV system. The statistics include statistics about self sufficiency, yield, unit prices, battery efficiency etc.

This README guides you through a simple installation and setup process. For an overview and a more detailed description of the sensors included in the *"Huawei Solar STAT package"*, please refer to the [Wiki Pages](https://github.com/JensenNick/huawei_solar_stat/wiki). The experienced Home Assistant user may find this guide banal - but this is to include all users, also the ones just starting out.

## Table of Content

1. [Before You Start](#1-before-you-start)
2. [Installation and Setup](#2-installation-and-setup)<br>
    2.1 [Package "installation"](#21-package-installation)<br>
    2.2 [Setup in Lovelace](#22-setup-in-lovelace)
3. [Known "bugs"](#3-known-bugs)

## 1. Before You Start
The custom sensors in the *"Huawei Solar STAT package"* are based on sensors provided by the *"Huawei Solar PEES package"*, which needs to be installed in Home Assistant before you start. Here is the link to my *"Huawei Solar PEES package"* and the latest release.

* **Huawei Solar PEES package** by JensenNick <https://github.com/JensenNick/huawei_solar_pees> including the `huawei_solar_pees.yaml` file (version v2.0.7 or more recent) and the `huawei_solar_input.yaml` file (version v1.0.1 or more recent).

Please note that the *"Huawei Solar STAT package"* is not an integration, it is a set of custom sensors I share.

> :exclamation: **It is good practise always to create a full backup before you start. Download / store the backup file outside of Home Assistant** :exclamation:

## 2. Installation and Setup
The custom sensors included in the *"Huawei Solar STAT package"* are available for download as a single file, intended to be "installed" as "packages". You can read more about packages in the Home Assistant documentation [Packages](<https://www.home-assistant.io/docs/configuration/packages/>).

### 2.1 Package "installation"

#### Install the package
Since this package requires the *"Huawei Solar PEES package"* to be installed first it is presumed that you have, created the directory/folder named `packages` in the `CONFIG` directory/folder (the main directory/folder) and added the link to the package folder in your `configuration.yaml` file according to the README for the *"Huawei Solar PEES package"*. In order to "install" the *"Huawei Solar STAT package"*,

* **Copy/paste the package files** [*"huawei_solar_stat.yaml"*](packages/huawei_solar_stat.yaml) into your `packages` directory/folder.

> :bulb: ***That is it! That is all the "installation" you need to do** in order to be up and running with all the custom sensors included in the "Huawei Solar STAT package".*

If you wish, you may download package files including the latest Release Note and supplemental documents like this README from the [Releases Page](https://github.com/JensenNick/huawei_solar_stat/releases), where you will also find previous releases.

#### Restart
Restart Home Assistant (not "Quick Reload") and refresh your browser (use the browser refresh button or F5 on Windows / Cmd+Shift+R on Mac).

### 2.2 Setup in Lovelace

#### Input Card
You need to provide a few user specific inputs for the *"Huawei Solar STAT package"*. This is done in a "Input Card" in Lovelace / GUI. Do not edit the `huawei_solar_input.yaml` file. First you need to create the "Input Card". It is assumed that you have created a **dashboard** and a **view** according to the README for the *"Huawei Solar PEES package"*

* **Add a new "Manual" card** in the "Input" view you created for the *"Huawei Solar PEES package Input Card"*
* **Copy/paste the code** from the [huawei_solar_input_card.md](https://github.com/JensenNick/huawei_solar_pees/blob/main/packages/huawei_solar_input_card.md) into the new "Manual" card. Make sure to delete/overwrite the predefined text `type: ''` in the card.
* **Click "Done" and refresh your browser.**

#### Battery Efficiency
The *"Huawei Solar STAT package"* includes statistic sensors that monitor the true round trip efficiency of your Huawei LUNA Battery which takes the efficiency of the inverter conversions, loss in the installation and standby consumption etc. into account. The true round trip efficiency is the efficiency based on how many kWh are produced (DC) / imported (AC) to charge the battery and how many kWh is available for usage (AC). 

> :bulb: I often see the term round trip efficiency misused - don't let yourself be fooled by this and the many iterations used to describe battery efficiency.

In the "Input Card" set the following parameters for the Battery Efficiency.

* **Rated Capacity** Enter the rated capacity in kWh of the Huawei LUNA Battery connected to your Huawei Solar PV system.
* **SOC Trigger** Enter the battery SOC percentage at which you would like the efficiency calculations to be triggered. The calculations will be triggered every time the `sensor.battery_state_of_capacity` passes this percentage. Preferably you should set this to a percentage at which your battery will pass frequently e.g. 50%.
* **Start Value Charge and Start Value Discharge** Enter the start values for charge and discharge must be set in order to take the charging and discharging done before the installation of the *"Huawei Solar STAT package"* into account and set a starting point for the efficiency calculations. 

Follow these steps to find the "Start Value Charge" and "Start Value Discharge".

* Set your SOC Trigger percentage.
* In Home Assistant, go to the History Tab and look up these entities, `sensor.energy_battery_charge`, `sensor.energy_battery_discharge` and `sensor.battery_state_of_capacity`.
* Decide on a date and time where the `sensor.battery_state_of_capacity` is equal to the SOC Trigger percentage you have chosen (in the example below I use SOC = 50 %). "Zoom in" by narrowing down the time frame (e.g. someting like 20 minutes). It does not matter if you choose a time while the battery is charging or discharging.
* Identify at which time the `sensor.battery_state_of_capacity` is turning equal to the SOC Trigger percentage and note down the state of the `sensor.energy_battery_charge` and `sensor.energy_battery_discharge`. These are your "Start Value Charge" and "Start Value Discharge". If the state is constant at the chosen time, you might need to get a reading outside of the time you have chosen.
* Go to the "Input Card" and enter the correct "Start Value Charge" and "Start Value Discharge".

![Battery Efficiency](/pictures/battery_efficiency.jpg)

> :bulb: In the example above the SOC turn to 50 % at 03:50:09. The state of Battery Charge is 77,75 kWh and the state of Battery Discharge is 65,21 kWh. These values are the "Start Value Charge" and "Start Value Discharge" respectively.

#### Yield Statistics
The *"Huawei Solar STAT package"* includes statistic sensors that monitor the output of your stings compared to the installed peak power. In the "Input Card" set the following parameters for the Yield Statistics.

* **Solar Panels Power** Enter the peak power of the installed type of solar panel.
* **Panels on inverter #1** Enter the number of panels connected to inverter #1.
* **Panels on inverter #2** Enter the number of panels connected to inverter #2.

## 3. Known "bugs"
None at the moment.
