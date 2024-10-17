# Huawei Solar Energy Management

[![GitHub Release][releases-shield]][releases]
[![GitHub Downloads][downloads-shield]][downloads]
[![License][license-shield]][license]
[![BuyMeCoffee][buymecoffeebadge]][buymecoffee]

![Icon](assets/icon.png)

## Derived from the Huawei Solar Battery Optimization Project

This integration was inspired by and derived from the [Huawei Solar Battery Optimization Project](https://github.com/heinoskov/huawei-solar-battery-optimizations), which was developed to optimize battery usage and maximize self-consumption in solar systems. While that project focuses on managing Huawei solar batteries, this integration adapts the smoothing techniques from it to handle any type of fluctuating sensor data, whether related to energy or other measurements.

## Summary

Maximize the potential of your Huawei solar battery system with this powerful Home Assistant package. By intelligently optimizing battery usage, solar production, and grid interaction, this solution helps you:

Significantly reduce your energy costs
Maximize returns on surplus solar energy
Minimize your carbon footprint
Increase your energy independence
Perfect for homeowners looking to make the most of their solar investment while contributing to a greener future.

Certainly! Here’s a more concise and streamlined version:

## Features

Dynamic Grid Export/Import Management:

- Avoids grid export when export prices are negative.
- Forces battery charging when import prices are negative.

EV Charging Optimization:

- Activates a dedicated TOU mode during EV charging.
- Prevents battery discharge while the EV is charging.

Seasonal Mode Switching:

- Uses Maximize Self Consumption (MSC) when solar production exceeds home consumption.
- Automatically selects between TOU and MSC based on season: TOU for winter/spring, MSC for summer.

Automatic Operational Adjustments:

- Maximizes solar self-consumption when solar production is high.
- Shifts modes based on time-of-use rates and seasonal conditions.

## Requirements

To use this package, you need the following integrations:

- [Huawei Solar integration by wlcrs](https://github.com/wlcrs/huawei_solar)
- [Solcast integration by oziee](https://github.com/BJReplay/ha-solcast-solar)
- [Energi Data Service integration by MTrab](https://github.com/MTrab/energidataservice)

### Optional integrations

- [Huawei Solar PEES package by JensenNick](https://github.com/JensenNick/huawei_solar_pees) (optional but recommended)
- [Smoothing Analytics Sensors by woopstar](https://github.com/woopstar/smoothing_analytics_sensors) (optional but recommended)

---

## Installation

### Method 1: HACS (Home Assistant Community Store)

1. In HACS, go to **Integrations**.
2. Click the three dots in the top-right corner, and select **Custom repositories**.
3. Add this repository URL and select **Integration** as the category:
   `https://github.com/woopstar/hsem`
4. Click **Add**.
5. The integration will now appear in HACS under the **Integrations** section. Click **Install**.
6. Restart Home Assistant.

---

### Method 2: Manual Installation

1. Copy the `hsem` folder to your `custom_components` folder in your Home Assistant configuration.
2. Restart Home Assistant.
3. Add the integration via the Home Assistant integrations page and configure your settings.

---

## Working Modes

This package supports several working modes to optimize your Huawei solar battery system:

### Maximize Self Consumption

**Description**: This mode prioritizes using the energy generated by your solar panels to power your home and charge your battery, minimizing the amount of energy drawn from the grid.

**Use Case**: Ideal for households looking to reduce their reliance on grid electricity and maximize the use of their solar energy production.

**When to Use**:

- During periods of high solar production
- When grid electricity prices are consistently high

### Time of Use (Battery Charge / Discharge)

**Description**: This mode optimizes battery charging and discharging based on time-of-use electricity rates. It charges the battery when electricity rates are low and discharges when rates are high.

**Use Case**: Perfect for users with time-of-use electricity tariffs who want to minimize their electricity costs.

**When to Use**:

- In areas with significant differences between peak and off-peak electricity rates
- To reduce strain on the grid during peak hours
- To take advantage of lower nighttime electricity rates for charging

**Default TOU Periods** (configured in this package)

- Off-peak (charging): 00:01 - 05:59 (all days)
- Peak (discharging): 06:00 - 10:00 (all days)
- Peak (discharging): 17:00 - 23:59 (all days)

These default periods are set to optimize battery usage based on typical daily electricity demand patterns. The system charges the battery during early morning hours when demand is typically low, and discharges during morning and evening peak hours. You can adjust these periods to match your specific utility's rate schedule or your household's energy consumption patterns.

### Fully Fed to Grid

**Description**: In this mode, all excess solar energy is fed back to the grid instead of being stored in the battery and in some circumstances will also drain the battery.

**Use Case**: Useful in scenarios where feeding energy to the grid is more beneficial than storing it. Especially if electricity price for selling is high.

**When to Use**:

- When grid feed-in tariffs are particularly high
- During periods of consistently high electricity spot prices
- If there's a need to reduce battery cycling to extend its lifespan

Note: This working mode is not in use by any automations at the moment, but script is added if needed.

[releases-shield]: https://img.shields.io/github/v/release/woopstar/hsem?style=for-the-badge
[releases]: https://github.com/woopstar/hsem/releases
[downloads-shield]: https://img.shields.io/github/downloads/woopstar/hsem/total.svg?style=for-the-badge
[downloads]: https://github.com/woopstar/hsem/releases
[license-shield]: https://img.shields.io/github/license/woopstar/hsem?style=for-the-badge
[license]: https://github.com/woopstar/hsem/blob/main/LICENSE
[buymecoffeebadge]: https://img.shields.io/badge/buy%20me%20a%20coffee-donate-FFDD00.svg?style=for-the-badge&logo=buymeacoffee
[buymecoffee]: https://www.buymeacoffee.com/woopstar
