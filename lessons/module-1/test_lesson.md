# Lesson 1: Testing the setup

## Objective
Test the manipulator setup

## Manipulator MG400

The Dobot MG400 is a compact robotic arm designed for desktop applications in automation, research, and education. With its lightweight structure and small footprint, the MG400 is suitable for a variety of tasks including pick-and-place, assembly, and precision operations.

More info about manipulator you can find [here](https://www.dobot-robots.com/products/desktop-four-axis/mg400.html).

## Programming manipulator with lua

Programming the Dobot MG400 with Lua script offers a powerful and flexible approach to automating tasks. Lua scripting allows you to write custom commands and functions to control the robotic arm with high precision and efficiency.

More information about manipulator programming and hardware can be found in the official manuals, available [here](https://www.dobot-robots.com/products/desktop-four-axis/mg400.html).

## RoboDK
RoboDK is a powerful simulation and offline programming software that enhances the capabilities of the Dobot MG400 robotic arm. By using RoboDK, you can create and simulate complex robotic tasks in a virtual environment before deploying them to the physical robot. One of the key features of RoboDK is its ability to generate Lua scripts for the MG400. After designing the desired robotic operations within RoboDK, you can export the simulation as Lua script, which can then be uploaded to the MG400. 

You can download RoboDK [here](https://robodk.com/download).


## Assignment
It is a test lesson with automatic verification. First, your code will be uploaded to the robot. The robot will then move to the starting point and begin executing your script. Your task is to move the manipulator to the coordinates: x=270, y=-120, z=-110. If the manipulator does not arrive at the specified point, the task will fail.

Here is a code example for moving the robot to the specified point:

Follow these instructions to upload the code to the robot:
1. Copy the code below:
    ```lua
    MovJ({coordinate={270, -120, -110, 0}})
    ```
2. Paste the code into the code editor.
3. Click the "Verify" button and wait for the result.

# Conclusion
In this lesson, you learned about the Dobot MG400 robotic arm and how to program it using Lua scripts. You also explored the benefits of using RoboDK for simulating and generating Lua scripts.
