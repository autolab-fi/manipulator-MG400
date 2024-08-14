# Lesson 2: Sandbox

## Objective
Experiment with a robot manipulator in a sandbox environment.

## Introduction
In this lesson, you'll be introduced to various commands and provided with a sample program to experiment with. The program will execute for 45 seconds, allowing you to observe the robot's movements and interactions.


## Commands List

### Motion Commands

**Point (P)** is an object that represents a specific position and orientation in the robot's workspace. It includes detailed information such as arm orientation, coordinates, joint angles, tool settings, and user settings. The point can be defined in two primary ways:

1. **Full Definition**:
   ```lua
   P1 = {
       armOrientation = "right",
       coordinate = {243, 106, -32, 0},
       joint = {0, 32, 32, 0, 0, 0},
       tool = 0,
       user = 0
   }
   ```

2. **Simplified Definition (using coordinates only)**:
   ```lua
   P1 = {coordinate = {243, 106, -32, 0}}
   ```

These definitions can be used in the motion commands as follows:

1. **MovJ(P1)** - Moves the robot to the target point `P1` using joint space interpolation. This command takes into account the joint angles defined in `P1`.
2. **MovL(P1)** - Moves the robot to the target point `P1` using linear interpolation, ensuring the robot follows a straight path to the specified coordinates.
3. **Sync()** - Waits for all previous commands to complete before proceeding to the next command, ensuring that the robot completes its current movement before starting a new one.


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

### More

These commands form the basis of robot control through scripting. For a more detailed list of available commands or additional information on how to use them, refer to the Lua section in the [CRStudio user guide](https://download.dobot.cc/2024/04/Dobot%20CRStudio%20User%20Guide%20%28MG400%26M1%20Pro%29_V4.13.0_2.14.0_20240311_en.pdf).


## Code example

This code example demonstrates a sequence of movements that can be programmed for the MG400:

```lua
-- Adjust speed parameters
local parameters={CP=1, SpeedJ=20, AccJ=10, SpeedL=20, AccL=10}

-- Command sequence to move the robot through various positions
MovL({coordinate={270, -120, -110, 0}}, parameters)
MovL({coordinate={220, -120, -110, 0}}, parameters)
MovL({coordinate={220, -70, -110, 0}}, parameters)
MovL({coordinate={270, -70, -110, 0}}, parameters)
MovL({coordinate={270, -120, -110, 0}}, parameters)

-- Rotate the R-Axis
MovL({coordinate={270, -120, -110, 90}}, parameters)
MovL({coordinate={270, -120, -110, 180}}, parameters)
MovL({coordinate={270, -120, -110, -90}}, parameters)

```

## Manipulator workspace

The workspace of the MG400 manipulator defines the maximum reach and operational limits of the robot. Here are the maximum points within its workspace that can be set in code:

X-Axis: -150 mm to +350 mm

Y-Axis: -150 mm to +150 mm

Z-Axis: -25 mm to +400 mm

Rotation (R-Axis): -360° to +360°

![workspace-1.png](https://github.com/autolab-fi/manipulator-mg400/blob/main/images/module-1/workspace-1.png?raw=true)

![workspace-2.png](https://github.com/autolab-fi/manipulator-mg400/blob/main/images/module-1/workspace-2.png?raw=true)

## Conclusion

By experimenting with these commands and the provided code, you can test manipulator.

