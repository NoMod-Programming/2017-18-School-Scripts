# Robotics Software

| Name                                    | Link to download                                      |
|-----------------------------------------|-------------------------------------------------------|
| RobotC for VEX Robotics                 | http://www.robotc.net/download/vexrobotics/           |
| VEXnet Firmware Upgrade Utility         | https://www.vexrobotics.com/vexedr/resources/firmware |
| VEXnet Key 2.0 Firmware Uprade Utility  | https://www.vexrobotics.com/vexedr/resources/firmware |
| Prolific USB Driver 3.2.0.0             | https://www.vexrobotics.com/vexedr/resources/firmware |
| PROS (Purdue Robotics Operating System) | https://pros.cs.purdue.edu/                           |

# Getting things to work

## Drivers

For some reason, Windows things it knows better than our manual installation of the Prolific USB-Serial driver. So we have to force it to use the right one. TO do this, press the Windows Key and the letter x on the keyboard, and click "Device Manager" on the menu that pops up. From there, open "Ports (COM & LPT)" and find a device with the word "Prolific" in it. Right click on it and update the drivers from a list of installed drivers. Then select the Prolific USB Driver with the version number of 3.2.0.0 (released in 2007).

## Cortexes

If a cortex stops working for whatever reason, first try removing all power to it. And then plugging it back in again. If that still doesn't fix it, use a thin allen wrench to press the "config" button and redownload code. If it still doesn't work, use the VEXnet Firmware Upgrade Utility to redownload the firmware back to the robot. This utility also works with Joysticks
