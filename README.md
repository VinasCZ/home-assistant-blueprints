# Home Assistant Blueprints

## IKEA Bilresa Scroll Wheel - 3 light control

Adapted from https://github.com/corentinnormand/ha-blueprints/blob/main/ikea_bilresa_scroll_wheel.yaml

Control brightness of up to 3 different lights / groups of lights.
The scroll-wheel must be set up in Matter mode to properly work with the three different modes.

#### Installation

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Fvinascz%2Fhome-assistant-blueprints%2Fmaster%2Fikea_bilresa_scroll_wheel.yaml)

Or manually import:

```
https://raw.githubusercontent.com/vinascz/home-assistant-blueprints/master/ikea_bilresa_scroll_wheel.yaml
```

#### Configuration

| Parameter                                 | Description                          | Default |
|-------------------------------------------|--------------------------------------|---------|
| **Light 1/2/3: Scroll Right/Left Entity** | Event entities for brightness scroll | -       |
| **Light 1/2/3: Button Press Entity**      | Event entity for brightness toggle   | -       |
| **Light 1/2/3: Target Light**             | Light to control                     | -       |
| **Light 1/2/3: Increase/Decrease Step**   | Brightness change per scroll (%)     | 10%     |
| **Light 1/2/3: Minimum**                  | Prevents turning off                 | 5%      |
| **Light 1/2/3: Maximum**                  | Maximum brightness                   | 100%    |
| **Transition Time**                       | Smoothing between values             | 0.2s    |
| **Automation Mode**                       | How to handle rapid scrolling        | restart |
