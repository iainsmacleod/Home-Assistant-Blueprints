# Motion-activated Light Blueprint for Home Assistant

This repository contains a Home Assistant automation blueprint that provides advanced motion-activated lighting control with multiple conditions and customization options.

https://github.com/iainsmacleod/Home-Assistant-Blueprints

If you like this blueprint and want to support me, feel free to leave a donation.

<a href="https://www.buymeacoffee.com/iainmacleod" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-blue.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>

## Features

- Control lights based on motion detection from one or more sensors
- Optional custom brightness and color settings
- Conditional activation based on the state of another entity
- Sun position awareness with configurable offset (day/night conditions)
- Blocking functionality to prevent activation in certain scenarios
- Configurable wait time after motion stops

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

- **Use Custom Brightness and Color**: Toggle to enable custom light settings
- **Brightness**: Light brightness level (0-255)
- **Color**: RGB color value for the lights

### Conditional Controls

- **Condition Entity**: Optional entity whose state will be checked before activating lights
- **Allowed States**: Comma-separated list of states for the condition entity
- **Sun Condition**: Option to activate only during day, night, or regardless of sun position
- **Sun Offset**: Time offset from sunrise/sunset in HH:MM format
- **Blocking Entity**: Entity that can prevent the automation from running
- **Blocking States**: States of the blocking entity that will prevent activation

## How It Works

1. When motion is detected, the blueprint checks all configured conditions
2. If conditions are met, lights turn on with either default or custom settings
3. When motion stops, the blueprint waits for the configured time
4. After the wait period, lights are turned off

## Advanced Functionality

The blueprint includes several advanced features:

- **Mode: restart** - Ensures the automation restarts if triggered again during execution
- **Multiple Condition Checks** - Evaluates entity states, sun position, and blocking conditions
- **Template Conditions** - Uses templating for flexible condition evaluation
- **Sun Position with Offset** - Allows fine-tuning of day/night detection

## Example Use Cases

- **Hallway Lighting**: Turn on hallway lights when motion is detected, but only at night
- **Bathroom Lights**: Activate with custom brightness based on time of day
- **Kitchen Under-cabinet Lighting**: Turn on when motion is detected but only if the main kitchen light is off
- **Outdoor Pathway Lights**: Activate only after sunset with a specific color and brightness

## Troubleshooting

If your automation isn't working as expected:

- Check that your motion sensors are correctly reporting motion
- Verify that any conditional entities have the expected states
- Ensure your sun offset format is correct (HH:MM)
- Check that blocking entities aren't preventing activation