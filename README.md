# Motion-activated Light with RGB/Temperature Control Blueprint for Home Assistant
Fork of iainsmacleod/Home-Assistant-Blueprints/advanced_motion_automation.yaml 
#### This fork retains most of the backend of the original blueprint, but provides means to select RGB or color temperature to set an RGBW light. 

Thanks to iainsmacleod - here is their donation link:

<a href="https://www.buymeacoffee.com/iainmacleod" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-blue.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>



# Motion-activated Light with RGB/Temperature Control Blueprint for Home Assistant
I created this fork for my own use, as I have some lights that refuse to cooperate over RGB and the original blueprint did not allow for control over color temperature. Note I am not a developer but doing this for my own needs - Happy for folks to use it if they find it helpful, but don't expect major updates. I will likely make small changes for my own needs over time.

This repository contains a Home Assistant automation blueprint that provides advanced motion-activated lighting control with multiple conditions and customization options.


https://github.com/smithad150/custom-motion-light-controller

## Features

- Control lights based on motion detection from one or more sensors
- Light can be operated as Toggle, RGB, or Temperature
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
- **Mode** : Must select Toggle, RGB, or Temperature mode for operation. 

### Conditional Controls

- **Brightness**: Required for RGB & Temperature modes.
- **Color**: Sets Color in RGB. Required for RGB mode.
- **Color Temperature**: Sets Color Temperature in Kelvins. Required for Temperature mode.
- **Condition Entity**: Optional entity whose state will be checked before activating lights
- **Allowed States**: Comma-separated list of states for the condition entity
- **Sun Condition**: Option to activate only during day, night, or regardless of sun position
- **Sun Offset**: Time offset from sunrise/sunset in HH:MM format
- **Blocking Entity**: Entity that can prevent the automation from running
- **Blocking States**: States of the blocking entity that will prevent activation

## How It Works

1. When motion is detected, the blueprint checks all configured conditions
2. If conditions are met, lights turn on with either RGB or color temperature settings
3. When motion stops, the blueprint waits for the configured time
4. After the wait period, lights are turned off

## Advanced Functionality

The blueprint includes several advanced features:

- **Mode: restart** - Ensures the automation restarts if triggered again during execution
- **Multiple Condition Checks** - Evaluates entity states, sun position, and blocking conditions
- **Template Conditions** - Uses templating for flexible condition evaluation
- **Sun Position with Offset** - Allows fine-tuning of day/night detection

## Troubleshooting

If your automation isn't working as expected:

- Check that your motion sensors are correctly reporting motion
- Verify that any conditional entities have the expected states
- Ensure your sun offset format is correct (HH:MM)
- Check that blocking entities aren't preventing activation
- Ensure your light can take the RGB or color temperature commands you select.
- If using the Temperature mode, your light must be able accept the value given (unit is Kelvins, range is HA default of 2700-6500). Some lights may behave unexpectedly if the value is outside their range.
