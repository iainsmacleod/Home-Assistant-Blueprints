# Motion-activated Light Blueprint for Home Assistant

This repository contains a Home Assistant automation blueprint that provides advanced motion-activated lighting control with multiple conditions and customization options.

https://github.com/iainsmacleod/Home-Assistant-Blueprints

If you like this blueprint and want to support me, feel free to leave a donation.

<a href="https://www.buymeacoffee.com/iainmacleod" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-blue.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>

## Features

- Control lights based on motion detection from one or more sensors
- **Three operating modes**: Simple Turn On, RGB Color Control, or Color Temperature Control
- **RGB Color Picker**: Visual color wheel interface for selecting custom colors (improvements by [@smithad150](https://github.com/smithad150/))
- **Color Temperature Control**: Slider-based Kelvin temperature selection (improvements by [@smithad150](https://github.com/smithad150/))
- Configurable brightness levels (0-255)
- Conditional activation based on the state of another entity
- Sun position awareness with configurable offset (day/night conditions)
- Blocking functionality to prevent activation in certain scenarios
- Configurable wait time after motion stops
- Support for both light and switch entities

## Installation

You can add this blueprint to your Home Assistant instance by:

1. Going to **Settings** > **Automations & Scenes** > **Blueprints**
2. Click the **Import Blueprint** button
3. Paste the URL of this repository and click **Preview**
4. Click **Import Blueprint**

## Configuration Options

### Required Settings

- **Motion Sensors**: One or more motion sensors that will trigger the lights
- **Lights**: One or more lights to be controlled by the automation
- **Wait Time**: Duration to keep lights on after motion stops (default: 120 seconds)

### Optional Settings

- **Mode**: Select how the light should be controlled:
  - **Turn On**: Simple on/off control with optional brightness
  - **RGB**: Full color control with visual color picker and brightness
  - **Temperature**: Color temperature control (Kelvin) with brightness
- **Brightness**: Light brightness level (0-255, default: 255)
- **Color**: RGB color selection using visual color picker (only used in RGB mode, default: white [255, 255, 255])
- **Color Temperature**: Kelvin temperature selection via slider (only used in Temperature mode, default: 4000K, range: 2700-6500K)

### Conditional Controls

- **Condition Entity**: Optional entity whose state will be checked before activating lights
- **Allowed States**: Comma-separated list of states for the condition entity
- **Sun Condition**: Option to activate only during day, night, or regardless of sun position
- **Sun Offset**: Time offset from sunrise/sunset in HH:MM format
- **Blocking Entity**: Entity that can prevent the automation from running
- **Blocking States**: States of the blocking entity that will prevent activation

## How It Works

1. When motion is detected, the blueprint checks all configured conditions (entity states, sun position, blocking entities)
2. If conditions are met, lights turn on based on the selected mode:
   - **Turn On mode**: Lights turn on with optional brightness setting
   - **RGB mode**: Lights turn on with selected color and brightness
   - **Temperature mode**: Lights turn on with selected color temperature and brightness
3. When motion stops, the blueprint waits for the configured time period
4. After the wait period, lights are automatically turned off

## Advanced Functionality

The blueprint includes several advanced features:

- **Mode: restart** - Ensures the automation restarts if triggered again during execution
- **Multiple Condition Checks** - Evaluates entity states, sun position, and blocking conditions
- **Template Conditions** - Uses templating for flexible condition evaluation
- **Sun Position with Offset** - Allows fine-tuning of day/night detection
- **Multiple Operating Modes** - Choose between simple on/off, RGB color control, or color temperature control
- **Visual Color Selection** - RGB color picker with color wheel interface
- **Flexible Entity Support** - Works with both light and switch entities

## Example Use Cases

- **Hallway Lighting**: Turn on hallway lights when motion is detected, but only at night (using Temperature mode for warm white)
- **Bathroom Lights**: Activate with custom brightness and color temperature based on time of day
- **Kitchen Under-cabinet Lighting**: Turn on when motion is detected but only if the main kitchen light is off (using RGB mode for accent colors)
- **Outdoor Pathway Lights**: Activate only after sunset with a specific RGB color and brightness
- **Bedroom Night Light**: Use Temperature mode with warm color temperature (2700-3000K) for night-time motion activation
- **Workshop Lighting**: Use RGB mode to set bright white or specific colors for task lighting

## Credits

Special thanks to [@smithad150](https://github.com/smithad150/) for improvements to the RGB color picker and color temperature selection functionality.

## Troubleshooting

If your automation isn't working as expected:

- Check that your motion sensors are correctly reporting motion
- Verify that any conditional entities have the expected states
- Ensure your sun offset format is correct (HH:MM)
- Check that blocking entities aren't preventing activation
- Verify that the selected mode (Turn On, RGB, or Temperature) matches your light's capabilities
- For RGB mode, ensure your lights support color changes
- For Temperature mode, ensure your lights support color temperature adjustments