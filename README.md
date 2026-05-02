# HA Dyson Card

`ha-dyson-card` is a lightweight Lovelace card for Dyson devices powered by the [`hass_dyson`](https://github.com/cmgrayb/hass-dyson) Home Assistant integration.

This project is intentionally dashboard-only. It does not replace the integration and depends on `hass_dyson` for device entities and data.

## Features

- Single-device Dyson control card with a simplified 360 direction dial
- Direction anchor, current aiming angle, and visible oscillation cone
- Quick cone-width presets for direct, 45°, 90°, 180°, and 350° sweep
- Derives the related Dyson device and companion entities from the selected fan entity
- Live debug section for validating discovered Dyson entities, raw states, attributes, and computed direction values
- Compact Home Assistant-style controls for Auto, night mode, fan speed, airflow direction, sleep timer, and filter life
- Clear live status for power, mode, fan speed, temperature, and humidity
- Works as a standalone custom card in Lovelace
- HACS-ready as a Dashboard / Plugin repo

## Requirements

- Home Assistant
- [`hass_dyson`](https://github.com/cmgrayb/hass-dyson) installed and configured
- A Dyson entity from that integration, typically a `fan.` entity

## Installation

### HACS

1. Open HACS
2. Add this repository as a custom repository
3. Category: `Dashboard`
4. Install `HA Dyson Card`
5. Refresh Home Assistant

## Usage

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
show_debug: true
```

## Notes

- The card derives the Dyson `device_id` and related entities from the selected fan entity using Home Assistant registries.
- The integration service currently accepts `lower_angle` and `upper_angle` in the `0-350` range.
- Auto uses the fan entity's `Auto` / `Manual` preset modes. Night mode uses the related night mode switch when present.
- Fan speed and airflow direction use the fan entity's standard `set_percentage` and `set_direction` services. Sleep timer uses `hass_dyson.set_sleep_timer`.
- `default_oscillation_angle` is used as a fallback when the live sweep width cannot be derived from Home Assistant.
- `show_debug` defaults to `true` while the card is being tested. Set it to `false` to hide the live debug panel.

## License

Apache-2.0
