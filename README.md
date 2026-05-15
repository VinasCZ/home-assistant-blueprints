# Home Assistant Blueprints

## IKEA Bilresa Scroll Wheel - 3 lights

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

## Philips Hue Tap Dial Switch

Controls a light using the Philips Hue Tap Dial Switch via ZHA.

- **Dial** — controls brightness of the target light
- **Button 1** — turns the light on/off; resets any counters back to zero when turned off
- **Button 2** — short/long press set a counter to 1 or 2; pressing again resets to 0
- **Button 3** — short press / hold increments a counter (resets to 0 at maximum); long press decrements (wraps to maximum at 0)
- **Button 4** — short/long press each trigger a separate `input_button` helper

#### Installation

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Fvinascz%2Fhome-assistant-blueprints%2Fmaster%2Fphilips_hue_tap_dial.yaml)

Or manually import:

```
https://raw.githubusercontent.com/vinascz/home-assistant-blueprints/master/philips_hue_tap_dial.yaml
```

#### Configuration

| Parameter                       | Description                                                                           | Default |
|---------------------------------|---------------------------------------------------------------------------------------|---------|
| **Hue Tap Dial Switch**         | The ZHA device                                                                        | —       |
| **Target Light**                | Light to control                                                                      | —       |
| **Minimum Brightness**          | Dial lower bound; 0% allows fully turning off via dial                                | 0%      |
| **Maximum Brightness**          | Dial upper bound                                                                      | 100%    |
| **Turn On Brightness**          | Brightness when turning on via button press                                           | 5%      |
| **Step Size**                   | Brightness change per dial tick                                                       | 1%      |
| **Dial Transition Time**        | Transition duration for dial adjustments                                              | 0.1s    |
| **Turn On/Off Transition Time** | Transition duration for button on/off                                                 | 0.5s    |
| **Button 2 Scene Helper**       | `counter` tracking button 2 state (0 = none, 1 = short, 2 = long); set maximum to 2   | —       |
| **Button 3 Scene Helper**       | `counter` tracking the active button 3 scene; set its maximum to the number of scenes | —       |
| **Button 4 Short Press Helper** | `input_button` pressed on button 4 short press                                        | —       |
| **Button 4 Long Press Helper**  | `input_button` pressed on button 4 long press                                         | —       |

#### Helpers setup

Create a `counter` helper for button 2 with maximum `2`, and a `counter` helper for button 3 with maximum equal to the
number of scenes to cycle through.

Create two `input_button` helpers for button 4 (one for short press, one for long press).
