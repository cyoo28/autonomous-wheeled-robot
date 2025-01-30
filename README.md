# Autonomous Wheeled Robot
For this project, an autonomous wheeled robot was designed that could be commanded to perform various tasks. This was completed as a course final project in December 2023.

## Problem Statement
This project required a wheeled robot to perform various tasks within a rectangular arena. These behavior states can be set wirelessly but must be completed autonomously. These tasks are as follows:
1. Following along the edges of the arena, avoiding collision with the walls
2. Navigate towards and differentiate between small objects using IR sensors
3. Navigate towards large objects using vive sensors

For the first task, the wheeled robot could implement a variety of different sensors, such as ultrasonic or time of flight sensors. These sensors could be used to detect when the robot has reached the end of a wall and must turn to follow the next one. They could also be used to detect when the robot has strayed too close or too far from the wall in order to correct its trajectory.

For the second task, there were multiple small objects placed randomly within the environment. Each object was equipped with flashing IR lights that could be sensed by the wheeled robot. These objects were split into 2 categories: target objects and distractor objects. The 2 types of objects could be differentiated by the frequency of the flashes. The robot needed to be able to differentiate between these frequencies in order to navigate towards the target objects and ignore the distractor objects.

For the last task, a vive base station was positioned over the center of the environment. The large object had a single, centered vive sensor that was used to transmit its position. The wheeled robot was allowed to have 2 vive sensors positioned in a way to determine its position and orientation. The robot could receive the large objects position to determine how to reach the large object.

## Solution Methodology
To complete the first task, the wheeled robot was equipped with a limit switch on the front of the chassis. The robot would then continue forward indefinitely until reaching the next wall. At this point, the wall would press down on the limit switch, causing the robot to maneuver such that it could then travel along the next wall.

To complete the second task, the wheeled robot was equipped with 2 phototransistors that were separated by a visual barrier. The robot would spin in place until it detected a signal from the IR lights on a small object. If the signal was visible in one phototransistor but not the other, then the robot would continue to spin until the signal could be detected in both and the robot was facing the object. The robot would then compute the frequency of the IR lights to determine whether or not the object is the desired target object. If it was the target object, the robot would then move forward until reaching its target. Otherwise, the robot would continue to search for other objects.

To complete the last task, the robot was programmed to receive the vive positional data of the large object. It also computed its own position relative to the large object in order to determine the necessary orientation. Once in the correct orientation, the robot would then move forward until it reaches the large object's position.

## Results
A basic webpage was created to send commands over user datagram protocol (UDP) to the robot. The robot would then perform the task that it was commanded to perform. While there were some issues with getting consistent sensor data, the robot was still able to complete the 3 tasks that it was required to perform. The code for this project can be reviewed in the code subdirectory. For a more detailed explanation of this project, please refer to [Autonomous Robot Performance Review.pdf](https://github.com/cyoo28/autonomous-wheeled-robot/blob/main/Autonomous%20Robot%20Performance%20Review.pdf).
