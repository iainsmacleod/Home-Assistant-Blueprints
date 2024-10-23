# Motion-activated Light with Conditions and Optional Settings

## Overview

This Home Assistant blueprint automates lighting based on motion detection. It allows for optional customization of brightness and color settings and includes conditions based on entity states and sun position. This makes it ideal for automating lights in your home with flexibility and precision.

## Features

- **Motion Detection**: Activates lights when motion is detected.
- **Customizable Lighting**: Optional settings for brightness and color.
- **Conditional Activation**: 
  - Based on the state of a specified entity (e.g., a mode selector for different times of day).
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
  - 
