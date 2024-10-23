# Motion-activated Light with Conditions and Optional Settings

## Overview

This Home Assistant blueprint automates lighting based on motion detection. It allows for optional customization of brightness and color settings and includes conditions based on a mode selector and sun position. This makes it ideal for automating lights in your home with flexibility and precision.

## Features

- **Motion Detection**: Activates lights when motion is detected.
- **Customizable Lighting**: Optional settings for brightness and color.
- **Conditional Activation**: 
  - Based on the state of a specified mode (`input_select` called "Mode").
  - Sun position (day or night).

## Blueprint Configuration

### Inputs

- **Motion Sensors**
  - **Name**: Motion Sensors
  - **Description**: Select one or more motion sensors.
  - **Type**: Binary Sensor (motion)

- **Lights**
  - **Name**: Lights
  - **Description**: Select one or more lights to control.
  - **Type**: Light Entity

- **Wait Time**
  - **Name**: Wait Time
  - **Description**: Time to leave the light on after the last motion is detected.
  - **Default**: 120 seconds
  - **Range**: 0 to 3600 seconds

- **Use Custom Brightness and Color**
  - **Name**: Use Custom Brightness and Color
  - **Description**: Enable to use custom brightness and color settings.
  - **Default**: False

- **Brightness**
  - **Name**: Brightness
  - **Description**: Set the brightness level (0-255).
  - **Default**: 255

- **Color**
  - **Name**: Color
  - **Description**: Set the color in RGB format.
  - **Default**: [255, 255, 255]

- **Condition Entity (Optional)**
  - **Name**: Condition Entity
  - **Description**: Select an entity to check its state (optional).
  
- **Allowed States for Condition Entity**
  - **Name**: Allowed States
  - **Description**: Enter the states that the condition entity should be in (comma-separated).

- **Sun Condition (Optional)**
  - **Name**: Sun Condition
  - **Description**: Select the sun condition to check.
  - **Options**: none, day, night

## Conditions

1. **Mode Condition**
   - This condition requires an `input_select` entity called "Mode," which represents different house modes such as morning, evening, or goodnight. The automation will only trigger if the "Mode" is set to one of the allowed states.

2. **Sun Position Condition**
   - The automation can be conditioned to only run during certain sun positions—specifically during the day or night.

## Usage Instructions

1. Import this blueprint into your Home Assistant instance.
2. Configure the inputs according to your setup:
   - Select your motion sensors and lights.
   - Adjust wait time, brightness, and color settings as needed.
   - Ensure you have an `input_select` entity named "Mode" with states that reflect different times or modes of your house.
   - Choose a sun condition if you want to restrict operation based on the time of day.

3. Save and activate the automation. The lights will turn on when motion is detected, subject to any conditions you've set.

## Notes

- Ensure that your motion sensors are properly configured in Home Assistant before using this blueprint.
- Create an `input_select` named "Mode" with desired states such as morning, evening, or goodnight for conditional operation.
- The sun condition requires that your Home Assistant instance has access to accurate sunrise/sunset times.
