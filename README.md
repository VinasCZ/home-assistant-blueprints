# Home Assistant Blueprints

## IKEA Bilresa Scroll Wheel - 3 lights (Simple)

Control brightness of up to 3 different lights / groups of lights.
Adapted from https://github.com/corentinnormand/ha-blueprints/blob/main/ikea_bilresa_scroll_wheel.yaml

The scroll-wheel must be set up in Matter mode. Select button 1's event entity — buttons 2–9 are derived automatically by replacing the button number. Requires the Device Online Helper blueprint to prevent spurious triggers on reconnect.

> **Note:** This blueprint relies on the button event entities not being renamed. If any entity has been renamed in HA, use the Full config version instead.

#### Installation

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Fvinascz%2Fhome-assistant-blueprints%2Fmaster%2Fikea_bilresa_scroll_wheel__simple.yaml)

Or manually import:

```
https://raw.githubusercontent.com/vinascz/home-assistant-blueprints/master/ikea_bilresa_scroll_wheel__simple.yaml
```

#### Configuration

| Parameter                 | Description                                                                                                 | Default  |
|---------------------------|-------------------------------------------------------------------------------------------------------------|----------|
| **Button 1 Event Entity** | Event entity for button 1 (e.g. `event.office_lights_control_remote_button_1`); buttons 2–9 derived from it | -        |
| **Device Online Helper**  | `input_boolean` managed by the Device Online Helper automation                                              | -        |
| **Light 1/2/3: Target**   | Light to control per mode                                                                                   | -        |
| **Brightness Step**       | Brightness change per scroll (%), applied to all lights                                                     | 5%       |
| **Scroll Right Action**   | Whether scrolling right increases or decreases brightness, applied to all lights                            | increase |
| **Minimum Brightness**    | Minimum brightness for all lights; 0% allows fully turning off via scroll                                   | 0%       |
| **Maximum Brightness**    | Maximum brightness for all lights                                                                           | 100%     |
| **Transition Time**       | Smoothing between values                                                                                    | 0.2s     |
| **Automation Mode**       | How to handle rapid scrolling                                                                               | restart  |

## IKEA Bilresa Scroll Wheel - 3 lights (Full config)

Adapted from https://github.com/corentinnormand/ha-blueprints/blob/main/ikea_bilresa_scroll_wheel.yaml

Full-configuration version with individual entity pickers and per-light step/min/max settings.

#### Installation

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Fvinascz%2Fhome-assistant-blueprints%2Fmaster%2Fikea_bilresa_scroll_wheel.yaml)

Or manually import:

```
https://raw.githubusercontent.com/vinascz/home-assistant-blueprints/master/ikea_bilresa_scroll_wheel.yaml
```

#### Configuration

| Parameter                                 | Description                                                                                       | Default |
|-------------------------------------------|---------------------------------------------------------------------------------------------------|---------|
| **Light 1/2/3: Scroll Right/Left Entity** | Event entities for brightness scroll                                                              | -       |
| **Light 1/2/3: Button Press Entity**      | Event entity for brightness toggle                                                                | -       |
| **Light 1/2/3: Target Light**             | Light to control                                                                                  | -       |
| **Light 1/2/3: Increase/Decrease Step**   | Brightness change per scroll (%)                                                                  | 5%      |
| **Light 1/2/3: Minimum**                  | Minimum brightness; 0% allows fully turning off via scroll                                        | 0%      |
| **Light 1/2/3: Maximum**                  | Maximum brightness                                                                                | 100%    |
| **Device Online Helper**                  | `input_boolean` managed by a separate automation to gate light actions when the device is offline | -       |
| **Transition Time**                       | Smoothing between values                                                                          | 0.2s    |
| **Automation Mode**                       | How to handle rapid scrolling                                                                     | restart |

## IKEA Bilresa - Device Online Helper

Manages an `input_boolean` that tracks whether the device is online. Use this alongside the 3 light control blueprint to
prevent spurious triggers when the device reconnects.

#### Installation

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Fvinascz%2Fhome-assistant-blueprints%2Fmaster%2Fikea_bilresa_device_online_helper.yaml)

Or manually import:

```
https://raw.githubusercontent.com/vinascz/home-assistant-blueprints/master/ikea_bilresa_device_online_helper.yaml
```

#### Configuration

| Parameter                | Description                                                                           | Default |
|--------------------------|---------------------------------------------------------------------------------------|---------|
| **Battery Type Sensor**  | Sensor reporting the device battery type; goes unavailable when the device is offline | -       |
| **Device Online Helper** | The `input_boolean` to manage                                                         | -       |

## IKEA Bilresa Scroll Wheel - brightness / colour / temperature

#### Installation

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Fvinascz%2Fhome-assistant-blueprints%2Fmaster%2Fikea_bilresa_scroll_wheel__colours.yaml)

Or manually import:

```
https://raw.githubusercontent.com/vinascz/home-assistant-blueprints/master/ikea_bilresa_scroll_wheel__colours.yaml
```