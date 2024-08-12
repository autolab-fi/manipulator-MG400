# Lesson 2: Sandbox

## Objective
Experiment with a robot manipulator in a sandbox environment.

## Introduction
In this lesson provided commands and program example. Program will be executing for 45 seconds.

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

### Program Control
1. **Sleep(time)** - Delay the execution of the next command. time: delay time, unit: ms
2. **Wait(time)** - Deliver the motion command with a delay, or deliver the next command with a delay after the current
motion is completed. time: delay time, unit: ms
3. **If...Then...Else** - Conditional statements for branching logic.
4. **Pause()** - Pause running the program. The program can continue to run only through software control or remote
control.
5. **Systime()** - Get the current system time

These commands form the basis of robot control through scripting.

If you need a more detailed list of available commands or further information on how to use them, you can refer to the Lua section in the [CRStudio user guide](https://download.dobot.cc/2024/04/Dobot%20CRStudio%20User%20Guide%20%28MG400%26M1%20Pro%29_V4.13.0_2.14.0_20240311_en.pdf).