# Lesson 2: Sandbox

## Objective
Experiment with a robot manipulator in a sandbox environment.

## Introduction
In this lesson, you'll be introduced to various commands and provided with a sample program to experiment with. The program will execute for 45 seconds, allowing you to observe the robot's movements and interactions.

## Commands list

### Motion Commands
1. **MoveJ()** - Moves the robot to a target point using joint space interpolation.
2. **MoveL()** - Moves the robot to a target point using linear interpolation.
3. **Sync()** - Waits for all previous commands to complete before proceeding to the next command.

### IO Commands
1. **DO(index,ON|OFF)** - Set the status of digital output port. ON/OFF: status of the DO port. ON: High level; OFF: Low level
2. **DOInstant(index,ON|OFF)** - Set the status of digital output port immediately regardless of the current command queue.
3. **ToolDI(index)** - Get the status of tool digital input port.
    Code example:
    ```lua
    if (ToolDI(1)==ON) then
        MovL(P1)
    end
    ```
    This script checks if the tool's digital input port 1 is ON, and if so, it moves the robot linearly to point P1.

### Program Control
1. **Sleep(time)** - Delay the execution of the next command. time: delay time, unit: ms
2. **Wait(time)** - Deliver the motion command with a delay, or deliver the next command with a delay after the current
motion is completed. time: delay time, unit: ms
3. **If...Then...Else** - Conditional statements for branching logic.
4. **Pause()** - Pause running the program. The program can continue to run only through software control or remote
control.
5. **Systime()** - Get the current system time


These commands form the basis of robot control through scripting. For a more detailed list of available commands or additional information on how to use them, refer to the Lua section in the [CRStudio user guide](https://download.dobot.cc/2024/04/Dobot%20CRStudio%20User%20Guide%20%28MG400%26M1%20Pro%29_V4.13.0_2.14.0_20240311_en.pdf).

## Manipulator workspace

The workspace of the MG400 manipulator defines the maximum reach and operational limits of the robot. Here are the maximum points within its workspace that can be set in code:

X-Axis: -150 mm to +350 mm

Y-Axis: -150 mm to +150 mm

Z-Axis: -25 mm to +400 mm

Rotation (R-Axis): -360° to +360°

![workspace-1.png](https://github.com/autolab-fi/manipulator-mg400/blob/main/images/module-1/workspace-1.png?raw=true)

![workspace-2.png](https://github.com/autolab-fi/manipulator-mg400/blob/main/images/module-1/workspace-2.png?raw=true)

## Code example

This code snippet demonstrates a sequence of movements that can be programmed for the MG400:

```lua
-- Adjust speed parameters
local parameters={CP=1, SpeedJ=20, AccJ=10, SpeedL=20, AccL=10}

-- Command sequence to move the robot through various positions
MovJ({0,0,0,0}, parameters)
MovJ({0,60,85,0}, parameters)
MovJ({0,70,58,-0}, parameters)
MovJ({-30,80,35,0}, parameters)
MovJ({-30.5,15,15,0}, parameters)

-- Rotate the R-Axis
MovJ({-40,70,75,0}, parameters)
MovJ({-40,70,75,90}, parameters)
MovJ({-40,70,75,-90}, parameters)

```

## Conclusion

By experimenting with these commands and the provided code, you can test manipulator.

