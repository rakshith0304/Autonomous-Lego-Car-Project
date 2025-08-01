# Autonomous LEGO Car with Manual Override

This project is a MATLAB-based control system for a LEGO Mindstorms EV3 robot car that can operate in both **autonomous** and **manual** modes. The car uses color, ultrasonic, and touch sensors to navigate its environment and make decisions accordingly.

## Demo Video
[![Watch on YouTube](https://img.youtube.com/vi/BWAP3AxwybM/0.jpg)](https://youtu.be/BWAP3AxwybM)

## Features

* **Dual Mode Operation**

  * **Autonomous Mode:** Triggered by black color detection.
  * **Manual Mode:** Triggered by green, blue, or yellow color detection.

* **Sensor Integration**

  * **Color Sensor (Port 2):** Determines mode and environment cues.
  * **Ultrasonic Sensor (Port 3):** Detects obstacles.
  * **Touch Sensor (Port 1):** Detects collisions.

* **Keyboard Control (Manual Mode)**

  * Arrow keys to drive
  * `W` / `S` to lift or lower the wheelchair mechanism
  * `B` to stop motors
  * `E` to exit the program

## How It Works

### Initialization

* Initializes keyboard input and sets color sensor mode.
* Main loop continuously checks for sensor inputs and user interaction.

### Manual Mode

Triggered by detecting:

* Green (`2`)
* Blue (`3`)
* Yellow (`4`, `7`)

In this mode, the robot can be controlled via keyboard inputs.

| Key         | Action                     |
| ----------- | -------------------------- |
| Up Arrow    | Move forward               |
| Down Arrow  | Move backward              |
| Left Arrow  | Turn left                  |
| Right Arrow | Turn right                 |
| W           | Lift wheelchair mechanism  |
| S           | Lower wheelchair mechanism |
| B           | Stop motors                |
| E           | Exit program               |

### Autonomous Mode

Triggered by detecting:

* Black (`1`)

Behavior depends on the state of the ultrasonic and touch sensors:

| Condition                | Action                           |
| ------------------------ | -------------------------------- |
| Distance ≤ 65, Touch = 0 | Move forward                     |
| Distance ≤ 65, Touch = 1 | Reverse briefly, then turn right |
| Distance > 65, Touch = 1 | Reverse briefly, then turn left  |
| Distance > 65, Touch = 0 | Turn left and move forward       |

### Red Light Detection

* If red (`5`) is detected, the robot pauses for 4 seconds before slowly moving forward again.

## Requirements

* LEGO EV3 Brick
* MATLAB with EV3 support package
* Sensors: Color (Port 2), Ultrasonic (Port 3), Touch (Port 1)
* Motors: A and B for wheels, C for lifting mechanism

## Setup Instructions

1. Connect sensors and motors to correct ports.
2. Run the script in MATLAB with EV3 connected via Bluetooth or USB.
3. Use colored markers to guide the robot and switch between modes.

## Notes

* Autonomous navigation relies on wall-following logic.
* Manual override gives full user control when necessary.
* Designed for experimental and educational purposes.
