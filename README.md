# HA Dyson Card

<p align="center">
  <img src=".github/images/ha-dyson-card-readme.svg" alt="HA Dyson Card" width="180">
</p>

[![Release](https://img.shields.io/github/v/release/thanhn062/ha-dyson-card?style=for-the-badge)](https://github.com/thanhn062/ha-dyson-card/releases)
[![License](https://img.shields.io/badge/license-Apache--2.0-green.svg?style=for-the-badge)](https://github.com/thanhn062/ha-dyson-card/blob/main/LICENSE)
[![HACS](https://img.shields.io/badge/HACS-Dashboard-41BDF5.svg?style=for-the-badge)](https://www.hacs.xyz/docs/use/repositories/type/dashboard/)
[![Validate](https://img.shields.io/github/actions/workflow/status/thanhn062/ha-dyson-card/validate.yaml?branch=main&style=for-the-badge&label=validate)](https://github.com/thanhn062/ha-dyson-card/actions/workflows/validate.yaml)
[![Home Assistant](https://img.shields.io/badge/Home%20Assistant-2024.8.0-blue.svg?style=for-the-badge&logo=home-assistant)](https://www.home-assistant.io/)

`HA Dyson Card` is a standalone Lovelace dashboard card for Dyson fans, purifiers, and heater fans exposed through [`hass_dyson`](https://github.com/cmgrayb/hass-dyson).

This repository contains only the frontend dashboard card. It does not replace the Dyson integration; it uses the entities and services exposed by `hass_dyson`.

## Features

- Direction wheel with drag-to-aim control
- Sweep dial presets for direct, 45°, 90°, 180°, and wide sweep
- Saved direction snapshots with icon, name, direction, sweep, and airflow speed
- Compact sensor badges for temperature, humidity, AQI, and filter life
- Expandable air-quality details for AQI, PM2.5, PM10, VOC, and NO2 when available
- Auto, night mode, airflow direction, sleep timer, fan speed, power, heat, fan-only, and target temperature controls
- Companion entity discovery from the selected Dyson fan entity
- Home Assistant theme-aware light and dark styling

## Requirements

- Home Assistant 2024.8.0 or newer
- [`hass_dyson`](https://github.com/cmgrayb/hass-dyson) installed and configured
- A Dyson `fan.` entity from that integration

## HACS Install

Default HACS inclusion is pending. For now, add this repository as a custom repository:

1. HACS -> top-right menu -> `Custom repositories`
2. Repository: `https://github.com/thanhn062/ha-dyson-card`
3. Category: `Dashboard`
4. Install `HA Dyson Card`
5. Refresh or reopen Home Assistant so the dashboard resource is loaded

HACS installs dashboard elements under `www/community/` and serves them through `/hacsfiles/`.

## Quick Start

Add the card to a dashboard:

```yaml
type: custom:ha-dyson-card
entity: fan.my_dyson
```

Optional fields:

```yaml
type: custom:ha-dyson-card
entity: fan.my_dyson
title: Bedroom Dyson
default_oscillation_angle: 90
```

## Notes

- The card derives related Dyson entities from the selected fan's Home Assistant device.
- Direction and sweep controls use the Dyson angle services exposed by `hass_dyson` when available.
- Fan speed and airflow direction use the fan entity's standard Home Assistant services.
- Sleep timer uses the `hass_dyson.set_sleep_timer` service.
- Heat and target temperature controls appear when a related Dyson climate entity is available.
- `default_oscillation_angle` is only used as a fallback when the live sweep width cannot be derived from Home Assistant.

## HACS Repository Shape

This repo follows the HACS Dashboard/plugin shape:

- `ha-dyson-card.js` lives at the repository root
- `hacs.json` declares `filename: ha-dyson-card.js`
- `.github/workflows/validate.yaml` runs HACS validation and JavaScript syntax checks

## License

Apache-2.0
